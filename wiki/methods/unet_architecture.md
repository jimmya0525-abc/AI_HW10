---
title: "U-Net 架構及其在超音波影像分割中的演進"
aliases: ["U-Net Architecture", "U-Net 醫學影像分割", "Attention U-Net", "Swin-Unet"]
category: "method"
tags: ["deep-learning", "segmentation", "cnn", "architecture", "skip-connection"]
last_updated: "2026-11-17"
sources: ["[[ronneberger2015_unet]]", "[[leclerc2019_camus]]", "[[vandenheuvel2018_hc18]]"]
---

# U-Net 架構及其在超音波影像分割中的演進

## 1. 核心機制：為什麼 U-Net 特別適合超音波？
[[ronneberger2015_unet|Ronneberger et al. (2015)]] 提出的 U-Net 至今仍是醫學超音波分割領域最關鍵的經典骨幹架構（Backbone）。
超音波影像具有以下獨特聲學痛點：
1. **[[speckle_noise|斑點噪聲]]** 導致局部對比度極低；
2. **聲束衰減與[[acoustic_shadowing|聲影]]** 導致器官深層或側壁輪廓中斷；
3. **低信噪比** 使標準 FCN 或語意分割模型在連續池化下遺失細小邊界。

**U-Net 的跳躍連接（Skip Connection）** 允許解碼器在進行高階語意判斷的同時，直接索取編碼端第一、二層保留的高解析度邊緣幾何資訊，實現對超音波微弱邊界的精細復原。

---

## 2. 演算法演進歷程
在超音波領域，U-Net 歷經數個關鍵迭代階段：

```
[原始 U-Net (2015)]
       │
       ▼
[Attention U-Net (2018)] ──> 引入注意力門控 (Attention Gate)，抑制背景斑點噪聲響應
       │
       ▼
[Swin-Unet (2021)]      ──> 引入滑動視窗自注意力 (Shifted Window)，增強長距離解剖依賴
       │
       ▼
[SAMUS (2023)]          ──> 結合自然影像大模型權重與超音波專用局部 CNN 分支
```

1. **Attention U-Net**：
   在跳躍連接中加入注意力門控（Attention Gate），利用深層粗粒度特徵作為門控信號，自動衰減淺層特徵圖中由[[speckle_noise|斑點雜訊]]引起的無關響應，集中強化腫瘤或心肌輪廓。
2. **Swin-Unet**：
   採用階層式 Vision Transformer 作為編解碼模組，利用移動視窗自注意力捕捉全域視野，有效緩解心臟或胎兒超音波中因局部聲影導致的斷裂問題。

---

## 3. 關鍵損失函數 (Loss Functions)
超音波分割通常面臨正負樣本極度不平衡問題（例如小腫瘤或薄心肌壁），標準交叉熵常被替換或結合為複合損失：
$$\mathcal{L}_{\text{total}} = \alpha \cdot \mathcal{L}_{\text{BCE}} + \beta \cdot \mathcal{L}_{\text{Dice}}$$
其中 Dice Loss 定義為：
$$\mathcal{L}_{\text{Dice}} = 1 - \frac{2 \sum_i p_i g_i + \epsilon}{\sum_i p_i^2 + \sum_i g_i^2 + \epsilon}$$
直接最大化預測輪廓與金標準的重疊交集（IoU）。

---

## 4. 關聯頁面 (Wiki Links)
- **奠基文獻**：[[ronneberger2015_unet|Ronneberger et al. 2015 U-Net]]
- **進階大模型**：[[samus_adapter|SAMUS 基礎模型適配]]
- **主要應用任務**：
  - [[breast_lesion_segmentation|乳腺腫瘤分割]]（[[busi_dataset|BUSI 資料集]]）
  - [[echocardiography_lvef|心臟超音波分割]]（[[camus_dataset|CAMUS 資料集]]）
  - [[fetal_biometry_measurement|胎兒頭圍自動量測]]（[[hc18_dataset|HC18 資料集]]）
