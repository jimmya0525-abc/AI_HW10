---
title: "超音波自監督對比學習 (Ultrasound Contrastive Learning, USCL)"
aliases: ["USCL Method", "Ultrasound SSL", "Acoustic Pretraining"]
category: "method"
tags: ["self-supervised-learning", "contrastive-learning", "pretraining", "ssl", "physics-ai"]
last_updated: "2026-11-17"
sources: ["[[jiao2020_uscl_contrastive]]", "[[wang2024_ultrasound_foundation_survey]]"]
---

# 超音波自監督對比學習 (USCL)

## 1. 為什麼自然影像自監督學習（SSL）在超音波上會翻車？
在自然電腦視覺中，對比學習（如 SimCLR、MoCo、BYOL）透過隨機數據增強（隨機色彩變換 Color Jittering、隨機高斯模糊、幾何旋轉裁切）構造正負樣本對，迫使模型學習「視角與光照不變性」。
然而，將這套邏輯生搬硬套至超音波影像會遭遇嚴重破壞：
1. **灰階回聲代表組織物理阻抗**：
   超音波的灰階數值非任意色彩，而是代表組織的聲阻抗差異（Acoustic Impedance Mismatch）。任意對比度反轉或色彩抖動會抹殺臨床關鍵的「無回聲（囊液）」、「低回聲（腫瘤）」與「強回聲（鈣化/骨質）」語意。
2. **扇形探頭幾何與深部衰減先驗**：
   淺層（Near Field）至深層（Far Field）存在天然的物理聲學衰減與空間發散特性。任意旋轉或破壞方向性會摧毀解剖拓撲。

---

## 2. USCL 的核心機制：聲學物理增強與時序關聯
[[jiao2020_uscl_contrastive|Jiao et al. (2020, 2023)]] 提出了專為超音波設計的自監督對比學習框架 **USCL**：

### 2.1 聲學物理專用數據增強 (Acoustic Augmentation)
- **斑點噪聲注入 (Speckle Simulation)**：依照瑞利分佈（Rayleigh Distribution）向特徵圖注入干涉波動，讓模型學習「穿越斑點雜訊、聚焦解剖實質」的能力。
- **深度指數衰減擾動 (Attenuation Perturbation)**：模擬探頭中心頻率與人體組織深度的衰減公式 $e^{-\alpha f z}$，使模型對不同增益設置（Gain/TGC）具備強健性。

### 2.2 時序連續性正樣本挖掘 (Temporal Continuity)
超音波掃查通常是動態視訊序列（Cine Loops）。在探頭平移或心動週期中：
- **相鄰時序幀作為正樣本對**：空間解剖結構高度一致，但組織微觀斑點已發生自然去相關（Decorrelation）。以此構建 InfoNCE 損失：
  $$\mathcal{L}_{\text{temporal}} = -\log \frac{\exp(\mathbf{z}_t^\top \mathbf{z}_{t+\Delta t} / \tau)}{\exp(\mathbf{z}_t^\top \mathbf{z}_{t+\Delta t} / \tau) + \sum_{k} \exp(\mathbf{z}_t^\top \mathbf{z}_k^- / \tau)}$$

---

## 3. 下游任務遷移增益
- 在完全無人工標註的情況下，於大規模超音波視訊庫上完成預訓練。
- 在僅提供 10% 稀缺標註樣本的下游任務（如 [[breast_lesion_segmentation|乳腺結節分割]] 與 [[standard_plane_detection|胎兒標準切面辨識]]）上，遷移效果超越傳統 ImageNet 預訓練權重 5-8% 以上。

---

## 4. 關聯頁面 (Wiki Links)
- **原始論文解析**：[[jiao2020_uscl_contrastive|USCL 論文精讀]]
- **基礎聲學概念**：[[speckle_noise|斑點噪聲物理機制]]
- **後續基礎模型綜述**：[[foundation_models_ultrasound|超音波基礎模型發展脈絡]]
