---
title: "SAMUS: 跨分支注意力與超音波基礎模型適配架構"
aliases: ["SAMUS Architecture", "Cross-Branch Attention", "CBA Adapter"]
category: "method"
tags: ["foundation-model", "sam", "adapter", "peft", "cross-attention"]
last_updated: "2026-11-17"
sources: ["[[lin2023_samus]]", "[[wang2024_ultrasound_foundation_survey]]"]
---

# SAMUS 架構與適配機制

## 1. 為什麼不能直接把 SAM 拿來做超音波？
Meta 的 Segment Anything Model (SAM) 雖然在自然影像具備強大的泛化與交互分割能力，但在醫學超音波領域面臨雙重瓶頸：
1. **聲學領域鴻溝 (Acoustic Domain Gap)**：
   自然照片具有清晰連續的物體邊緣與平滑色彩對比；超音波則充斥[[speckle_noise|斑點噪聲]]、[[acoustic_shadowing|聲影]]衰減與微弱界面回聲。SAM 的全局自注意力無法區分生理組織界面的高頻回聲與噪聲干涉，常導致分割邊界隨意擴散。
2. **計算代價與臨床可行性**：
   原始 SAM 使用 ViT-H 骨幹（6.36 億參數），記憶體佔用極大，無法在資源受限的床邊掌上型超音波（POCUS）設備中執行即時推理。

---

## 2. 雙分支混合架構設計
為解決上述難題，[[lin2023_samus|Lin et al. (2023)]] 提出了 **SAMUS**，其架構核心為「雙分支（Dual-Branch）+ 跨分支注意力（Cross-Branch Attention, CBA）」：

```
輸入超音波影像 ──┬──> [凍結的 ViT 影像編碼器 (Frozen SAM)] ──> 全局拓撲語意特徵
                │                                                    │
                │                                         [CBA 跨分支適配器]
                │                                                    │
                └──> [輕量級 CNN 空間編碼分支] ─────────────> 局部高頻聲學邊緣特徵
                                                                     │
                                                                     ▼
                                                         [輕量 Mask 解碼器]
                                                                     │
                                                                     ▼
                                                          精確超音波病灶輪廓
```

### 2.1 凍結的大模型分支 (Frozen ViT Backbone)
完全鎖定預訓練好的 SAM ViT 權重，保留其在大規模自然資料集所習得的強大幾何形狀與部件整體結構認知，避免在少量超音波樣本微調時發生災難性遺忘（Catastrophic Forgetting）。

### 2.2 輕量卷積分支 (CNN Branch)
專門處理由原始 RF 訊號重建的超音波高解析度灰階幀，透過小卷積核提取高頻邊界梯度與組織回聲特徵，彌補 Vision Transformer 缺乏局部歸納偏置（Inductive Bias）的弱點。

### 2.3 跨分支注意力適配模組 (CBA Module)
插入在 ViT 區塊之間，將 CNN 分支捕捉到的局部聲學邊界資訊作為 Key 與 Value，與 ViT 的 Query 進行交叉注意力計算，動態導引大模型權重關注真實的超音波解剖邊界。

---

## 3. 參數高效微調 (PEFT) 效益
- 整個訓練過程**僅更新約 3.2% 的模型參數**。
- 支援靈活的提示機制：臨床醫師單點點擊（Single Click）、病灶外框選取（Bounding Box），或全自動無提示推論（Prompt-free）。
- 在 [[busi_dataset|BUSI]]、[[camus_dataset|CAMUS]] 等多中心超音波資料集上，分割 Dice 指標全面超越原始 SAM 與 MedSAM。

---

## 4. 關聯頁面 (Wiki Links)
- **原始論文解析**：[[lin2023_samus|SAMUS 論文筆記]]
- **基礎模型領域綜述**：[[foundation_models_ultrasound|超音波基礎模型現狀與挑戰]]
- **基礎比較架構**：[[unet_architecture|U-Net 分割]]
