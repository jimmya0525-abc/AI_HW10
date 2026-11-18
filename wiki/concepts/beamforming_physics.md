---
title: "超音波波束成形 (Beamforming) 物理與射頻訊號處理"
aliases: ["Beamforming", "波束合成", "DAS", "RF Channel Data", "PSF"]
category: "concept"
tags: ["physics", "beamforming", "rf-signal", "signal-processing", "resolution"]
last_updated: "2026-11-17"
sources: ["[[luchies2018_dnn_beamforming]]", "[[errico2015_ulm_super_resolution]]"]
---

# 超音波波束成形 (Ultrasound Beamforming)

## 1. 波束成形的基本使命
超音波探頭由數十至數百個壓電晶片陣元（Piezoelectric Transducer Elements）排列而成。當探頭向人體發射聲波脈衝時，組織散射回來的回聲到達各個陣元存在微小時間差。
**波束成形（Beamforming）**的任務是：接收多個通道的原始射頻信號（Pre-beamformed RF Channel Data），透過精確計算聲程幾何飛行時間差進行對齊與加權疊加，合成空間中特定焦點的高對比回聲信號，最終重建出人眼可判讀的 B-mode 灰階解剖影像。

---

## 2. 經典延遲相加法 (Delay-and-Sum, DAS)
DAS 是過去數十年商用超音波設備的基石架構。針對空間中任意目標點 $\mathbf{x}_p = (x_p, z_p)$，第 $m$ 個陣元接收到該點回聲的時間延遲為：
$$\tau_m(\mathbf{x}_p) = \frac{d_{\text{tx}}(\mathbf{x}_p) + d_{\text{rx}}(\mathbf{x}_p, m)}{c_0}$$
其中 $c_0$ 通常假設為人體軟組織均勻平均聲速（常取 $1540\,\text{m/s}$）。合成信號為：
$$s(t, \mathbf{x}_p) = \sum_{m=1}^{M} w_m \cdot y_m(t - \tau_m(\mathbf{x}_p))$$
其中 $w_m$ 為變跡加權窗函數（Apodization，如 Hanning 或 Hamming 窗），用於壓制天線陣列旁瓣。

---

## 3. 傳統物理限制與痛點
1. **相位像差 (Phase Aberration)**：
   人體各組織層聲速差異顯著（皮下脂肪 $c \approx 1450\,\text{m/s}$，肌肉 $c \approx 1580\,\text{m/s}$）。假設單一均勻聲速導致延遲計算錯誤，引發破壞性相位干涉，導致波束散焦、側向解析度惡化。
2. **旁瓣偽影與雜波 (Clutter & Side-lobes)**：
   高回聲組織引發的離軸散射會經由探頭旁瓣洩漏進主焦點，填塞心室或血管管腔等無回聲區域。
3. **點擴散函數 (Point Spread Function, PSF)**：
   系統成像解析度受探頭頻寬與孔徑物理尺寸限制，單點散射子在影像上呈現橢圓狀 PSF，制約了微米級病灶的觀測能力。

---

## 4. 深度學習對波束成形的顛覆
如 [[luchies2018_dnn_beamforming|Luchies & Byram (2018)]] 所示，現代 AI 不再侷限於後端影像後處理，而是直接下沉至前端 RF 通道數據，以神經網路直接學習非線性空間濾波映射：
- 取代高運算量矩陣求逆的最小方差（Capon MV）自適應波束成形。
- 顯著縮減 PSF 側向寬度，抑制深部組織雜波達 15 dB 以上。

---

## 5. 關聯頁面 (Wiki Links)
- **方法進展**：[[deep_beamforming|深度學習波束成形]]
- **突破極限**：[[ultrasound_super_resolution|超解析度顯微成像 (ULM)]]
- **原始論文**：[[luchies2018_dnn_beamforming|Luchies & Byram 2018 論文解析]]
