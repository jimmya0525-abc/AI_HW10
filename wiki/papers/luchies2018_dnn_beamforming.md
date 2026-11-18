---
title: "DNN Beamforming: 深度學習驅動的超音波波束成形 (Luchies & Byram, 2018)"
aliases: ["DNN Beamforming", "Luchies 2018"]
category: "paper"
tags: ["ultrasound", "beamforming", "physics-ai", "signal-processing", "radio-frequency"]
last_updated: "2026-11-17"
sources: ["[[raw/papers/08_luchies2018_dnn_beamforming.md]]"]
---

# Deep Neural Networks for Ultrasound Beamforming

- **作者**：Adam C. Luchies, Brett C. Byram
- **發表場合**：IEEE Transactions on Ultrasonics, Ferroelectrics, and Frequency Control (TUFFC), 2018
- **原始文獻依據**：[[raw/papers/08_luchies2018_dnn_beamforming.md]]

---

## 1. 論文核心貢獻
傳統超音波成像的前端訊號處理仰賴於**延遲相加法 (Delay-and-Sum, DAS)**，其假設組織內部聲速均勻恆定。但在人體複雜脂肪與肌肉分層中，聲速非均勻性會引發嚴重的**相位像差 (Phase Aberration)** 與離軸聲學雜波（Clutter）。本文首創提出**將深度神經網路（DNN）直接置於射頻通道數據（Pre-beamformed RF Channel Data）之上**，跳過傳統矩陣求逆計算，實現非線性、低雜波的高對比波束成形。

---

## 2. 演算法架構與訊號原理
1. **DAS 的缺陷**：
   $$s(t, \mathbf{x}) = \sum_{m=1}^{M} w_m y_m(t - \tau_m(\mathbf{x}))$$
   DAS 僅做簡單加權相加，面對強烈側向散射波時，無法區分主瓣（Main-lobe）與旁瓣（Side-lobe），造成低回聲囊腫內部充滿虛假雜波。
2. **深度學習非線性映射**：
   DNN 直接接收 $M$ 個探頭陣元的原始 RF 時序信號向量，訓練目標為擬合無雜波、高對比度的理想點目標回聲。
3. **性能提升指標**：
   - 對比度雜訊比（CNR）較傳統 DAS 提升高達 14.8 dB。
   - 橫向點目標半高全寬（FWHM）縮小 40-50%，顯著增強微小病灶的辨析度。
   - 運算複雜度由自適應波束成形（如 Capon MV）的 $O(M^3)$ 降至前向神經網路矩陣乘法，具備邊緣硬體即時化潛力。

---

## 3. 關聯頁面 (Wiki Links)
- **核心概念**：[[beamforming_physics|超音波波束成形聲學原理]]
- **方法模型**：[[deep_beamforming|深度學習波束成形技術]]
- **物理噪聲源**：[[speckle_noise|斑點噪聲與聲學混響]]
