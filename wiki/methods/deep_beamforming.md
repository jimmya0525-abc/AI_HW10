---
title: "深度學習波束成形 (Deep Learning Beamforming) 與前端信號處理"
aliases: ["Deep Beamforming", "DNN Beamformer", "RF Deep Learning"]
category: "method"
tags: ["beamforming", "rf-signal", "deep-learning", "signal-processing", "hardware-acceleration"]
last_updated: "2026-11-17"
sources: ["[[luchies2018_dnn_beamforming]]", "[[errico2015_ulm_super_resolution]]"]
---

# 深度學習波束成形 (Deep Learning Beamforming)

## 1. 前端訊號重構的範式轉移
在傳統超音波系統管線中，人工智慧演算法通常僅作用於**終端 B-mode 影像**（經過檢波、對數壓縮與掃描轉換後）。然而，此時大量原始回聲的相位、頻率及同調性資訊已經徹底遺失。
[[luchies2018_dnn_beamforming|Luchies & Byram (2018)]] 樹立了將深度學習直接置於**未成形射頻通道數據（Pre-beamformed RF Channel Data）**上的全新技術路徑。

---

## 2. 演算法架構與訊號流管線

```
壓電探頭陣列 (M 個陣元)
       │
       ▼ (接收未壓縮 RF 電信號)
幾何幾何延遲計算 (Time Delay Correction)
       │
       ▼ (時延通道矩陣 Y ∈ R^{M x K})
[深度神經網路波束成形器 (DNN / 1D-CNN)]
       │ (學習非線性干涉消除與自適應加權)
       ▼
合成高解析度無雜波 RF 射線 (Clean RF A-line)
       │
       ▼ (希爾伯特變換 & 對數壓縮)
超高對比度 B-mode 超音波影像
```

### 2.1 學習目標與損失設計
神經網路輸入為 $M$ 個探頭陣元經過粗略幾何延遲校正後的通道矩陣 $\mathbf{Y} \in \mathbb{R}^{M \times K}$。訓練目標通常採用複合損失函數：
$$\mathcal{L} = \|\hat{s}(t) - s_{\text{ideal}}(t)\|_2^2 + \lambda \cdot \mathcal{L}_{\text{contrast}}$$
其中 $s_{\text{ideal}}(t)$ 是由聲學物理模擬軟體（如 Field II）或超高精度相干平面波合成（Coherent Plane Wave Compounding）生成的高對比無旁瓣理想信號。

---

## 3. 相較於傳統方法的重大飛躍
1. **擺脫矩陣求逆計算瓶頸**：
   傳統自適應波束成形（如最小方差法 Minimum Variance / Capon）需即時計算 $M \times M$ 協方差矩陣的逆矩陣，時間複雜度高達 $\mathcal{O}(M^3)$，在臨床 128 或 256 通道探頭上極難即時運算。神經網路將複雜的非線性優化轉化為固定的前向矩陣乘法，具備 FPGA/GPU 硬體即時加速能力。
2. **抵抗聲速非均勻性**：
   神經網路透過卷積核捕捉多通道回聲波形的相位畸變規律，自主修正組織異質性引起的相位像差（Phase Aberration）。
3. **消除黑洞偽影**：
   在微小囊腫與血管腔內部，傳統 DAS 的側向旁瓣回聲滲漏被有效切除，對比度雜訊比（CNR）顯著提升 10-15 dB。

---

## 4. 關聯頁面 (Wiki Links)
- **基礎聲學概念**：[[beamforming_physics|超音波波束成形原理與 DAS]]
- **原始研究**：[[luchies2018_dnn_beamforming|Luchies & Byram 2018 論文筆記]]
- **超解析度關聯**：[[ultrasound_super_resolution|超解析度顯微成像 (ULM)]]
