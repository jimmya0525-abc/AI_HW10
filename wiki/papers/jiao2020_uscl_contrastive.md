---
title: "USCL: 結合超音波物理特性的自監督對比學習 (Jiao et al., 2020/2023)"
aliases: ["USCL", "Jiao 2020"]
category: "paper"
tags: ["ultrasound", "self-supervised-learning", "contrastive-learning", "video-pretraining"]
last_updated: "2026-11-17"
sources: ["[[raw/papers/09_jiao2020_uscl_contrastive.md]]"]
---

# Self-Supervised Learning for Ultrasound Video Representation (USCL)

- **作者**：Jianbo Jiao, Rong Rong, Shengfeng He, Kwang-Ting Cheng 等
- **發表場合**：MICCAI 2020 / IEEE Transactions on Medical Imaging (TMI), 2023
- **原始文獻依據**：[[raw/papers/09_jiao2020_uscl_contrastive.md]]

---

## 1. 論文核心貢獻與動機
在醫學超音波領域，高品質醫師像素級標註成本高昂且主觀變異性大。自然影像中的自監督學習（如 SimCLR、MoCo）直接搬移至超音波時表現欠佳。
- **痛點**：自然影像增強策略（如隨機色彩抖動、旋轉裁切）會徹底破壞超音波由組織聲阻抗決定的明暗回聲物理語意（無回聲、低回聲、強回聲）以及扇形探頭的深部幾何先驗。
- **USCL 解決方案**：設計專門符合超音波物理特性的數據增強模組（Acoustic-aware Augmentation）與視訊時序對比學習（Temporal Contrastive Learning）機制。

---

## 2. 聲學物理增強與時序對比機制
1. **聲學物理增強 (Acoustic Augmentation)**：
   - **斑點噪聲模擬**：注入瑞利分佈（Rayleigh）噪聲，模擬聲束干涉波動。
   - **深度聲學衰減模擬**：沿深度軸 $z$ 施加指數級信號衰減 $e^{-\alpha f z}$，使模型適應探頭深度衰減。
2. **時序對比目標 (Temporal InfoNCE)**：
   將相鄰心搏或探頭滑動過程中的時序連續幀作為天然正樣本對（Positive Pairs）——彼此共享解剖結構拓撲，但具備天然的斑點噪聲去相關與探頭角度擾動。
3. **成果**：在僅使用 10% 標註數據的下游任務中（乳腺結節分割、胎兒標準切面分類），微調表現顯著優於 ImageNet 預訓練與傳統從頭訓練架構。

---

## 3. 關聯頁面 (Wiki Links)
- **方法模型**：[[ultrasound_contrastive_learning|超音波專用自監督對比學習]]
- **聲學概念**：[[speckle_noise|斑點噪聲與回聲特性]]
- **下游應用**：[[breast_lesion_segmentation|乳腺結節分割]]、[[standard_plane_detection|超音波標準切面辨識]]
