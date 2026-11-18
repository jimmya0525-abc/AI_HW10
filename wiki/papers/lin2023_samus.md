---
title: "SAMUS: 面向超音波影像分割的通用基礎模型微調 (Lin et al., 2023)"
aliases: ["SAMUS", "Lin 2023"]
category: "paper"
tags: ["ultrasound", "foundation-model", "sam", "adapter", "parameter-efficient-fine-tuning"]
last_updated: "2026-11-17"
sources: ["[[raw/papers/04_lin2023_samus.md]]"]
---

# SAMUS: Adapting Segment Anything Model for Clinically-Friendly Ultrasound Image Segmentation

- **作者**：Xian Lin, Xiangde Luo, Yang Chen, Guanbin Li, Guoyan Zheng 等
- **發表場合**：IEEE Transactions on Medical Imaging (TMI), 2023 / arXiv:2309.06824
- **原始文獻依據**：[[raw/papers/04_lin2023_samus.md]]

---

## 1. 論文核心貢獻與痛點分析
Meta 發布的 **SAM (Segment Anything Model)** 在自然影像展現出驚人的 Zero-shot 交互分割能力，但直接應用於超音波影像時出現嚴重效能雪崩（Dice 驟降 20-30%）。
- **失靈原因**：自然影像具有連續且高對比度輪廓，而超音波充斥[[speckle_noise|斑點噪聲]]、[[acoustic_shadowing|聲影]]、深部信號衰減與模糊邊界；SAM 的全局自注意力機制往往誤將噪聲偽影視為分割對象。
- **計算限制**：SAM ViT-H 參數高達 6.36 億，無法在基層臨床或掌上型超音波（POCUS）邊緣端即時推理。
- **SAMUS 解法**：提出兼具**參數高效微調（PEFT）**與**局部聲學特徵注入**的專用架構。

---

## 2. 雙分支交叉注意力架構 (Dual-Branch Architecture)
1. **凍結基礎 Transformer 分支 (Frozen SAM Branch)**：保留在千萬級自然影像預訓練的大規模拓撲感知權重。
2. **輕量級 CNN 空間分支 (CNN Spatial Branch)**：平行引入輕量卷積層，專門捕捉超音波原始幀的高頻聲學邊界梯度與組織回聲特徵。
3. **跨分支注意力適配模組 (Cross-Branch Attention Adapter, CBA)**：
   將 CNN 提取的聲學邊界先驗動態注入 ViT 區塊中，僅更新約 3.2% 的模型參數，大幅降低訓練與儲存成本。

---

## 3. 跨器官基準表現與成果
在涵蓋乳腺（[[busi_dataset|BUSI]]）、心臟（[[camus_dataset|CAMUS]]）、甲狀腺（TN3K）等 7 個跨中心資料集評測中：
- 平均 Dice 達 88.4%，超越 MedSAM 4.2%，更大幅領先原始 SAM 達 15.6%。
- 支援「點提示（Point Prompt）」、「邊界框（BBox）」與「無提示自動模式（Prompt-free）」，為超音波基礎模型樹立全新典範。

---

## 4. 關聯頁面 (Wiki Links)
- **方法詳解**：[[samus_adapter|SAMUS 交叉注意力適配架構]]
- **基礎模型綜述**：[[foundation_models_ultrasound|超音波領域基礎模型技術發展]]
- **被測資料集**：[[busi_dataset|BUSI 資料集]]、[[camus_dataset|CAMUS 心臟資料集]]
