---
title: "超音波人工智慧發展歷程：從聲學物理、任務專用 CNN 到多模態基礎模型"
aliases: ["Ultrasound AI Evolution", "超音波 AI 技術演進史", "技術全景綜述"]
category: "synthesis"
tags: ["synthesis", "roadmap", "survey", "history", "foundation-models"]
last_updated: "2026-11-17"
sources: [
  "[[ronneberger2015_unet]]",
  "[[aldhabyani2020_busi]]",
  "[[leclerc2019_camus]]",
  "[[lin2023_samus]]",
  "[[ouyang2020_echonet_dynamic]]",
  "[[vandenheuvel2018_hc18]]",
  "[[errico2015_ulm_super_resolution]]",
  "[[luchies2018_dnn_beamforming]]",
  "[[jiao2020_uscl_contrastive]]",
  "[[wang2024_ultrasound_foundation_survey]]"
]
---

# 超音波人工智慧技術演進全景

## 1. 綜述背景
醫學超音波（Ultrasound）是現代醫療體系中最普及、無游離輻射、低成本且具備極高即時性（Real-time）的影像技術。然而，其嚴重的操作者依賴性、探頭移動引發的幾何畸變、組織界面微弱回聲以及[[speckle_noise|斑點噪聲]]和[[acoustic_shadowing|聲影]]，長期困擾著影像判讀。
回顧過去十餘年，超音波 AI 研究經歷了顯著的三個代際躍遷：

```
[古典與物理奠基期 (2015以前)]
  - 傳統統計濾波、水平集 (Level Set)、手動特徵工程 (Haralick 紋理)
  - 突破：[[errico2015_ulm_super_resolution|ULM 超快顯微成像 (Nature 2015)]] 突破繞射極限
        │
        ▼
[第一波：專門任務的監督式深度學習 (2015 - 2020)]
  - 骨幹核心：[[ronneberger2015_unet|U-Net (2015)]] 引入跳躍連接挽救聲學邊界
  - 標竿資料集井噴：[[vandenheuvel2018_hc18|HC18 產前頭圍 (2018)]]、[[leclerc2019_camus|CAMUS 心臟 (2019)]]、[[aldhabyani2020_busi|BUSI 乳腺 (2020)]]
  - 訊號前端探索：[[luchies2018_dnn_beamforming|DNN 波束成形 (2018)]] 下沉至射頻 RF 訊號
        │
        ▼
[第二波：動態時空視訊與聲學自監督學習 (2020 - 2022)]
  - 視訊心動圖突破：[[ouyang2020_echonet_dynamic|EchoNet-Dynamic (Nature 2020)]] 萬例視訊 beat-to-beat 建模
  - 聲學物理預訓練：[[jiao2020_uscl_contrastive|USCL (2020/2023)]] 利用時序連續性與斑點噪聲增強自監督表徵
        │
        ▼
[第三波：超音波專用大模型與多模態時代 (2023 - 現在)]
  - 基礎模型適配：[[lin2023_samus|SAMUS (2023)]] 雙分支跨注意力適配 SAM 解決領域落差
  - 多中心標竿與大模型綜述：[[wang2024_ultrasound_foundation_survey|Wang et al. (2024)]] 定義通用 US-FM 範式
```

---

## 2. 關鍵範式轉變深度解析

### 2.1 從「圖像後處理」下沉至「聲學物理前端」
- **過去**：電腦視覺學者大多將超音波 B-mode 影像視為普通灰階圖片，使用常規 CNN 處理，忽視了探頭陣元、聲束延遲與相位干涉的物理源頭。
- **演進**：[[luchies2018_dnn_beamforming|深度學習波束成形]] 與 [[errico2015_ulm_super_resolution|ULM]] 證明，AI 深入至原始射頻（RF）通道時，能消除離軸旁瓣雜波，甚至打破光學/聲學波長繞射極限。

### 2.2 從「靜態孤立單幀」躍遷至「連續時空視訊流」
- **過去**：受限於標註成本，如 [[leclerc2019_camus|CAMUS]] 僅標註舒張末期（ED）與收縮末期（ES）兩張靜態幀，依賴人工挑選，主觀誤差大。
- **演進**：[[ouyang2020_echonet_dynamic|EchoNet-Dynamic]] 引入時空解耦卷積 R(2+1)D，直接吞吐整段連續心搏視訊；[[jiao2020_uscl_contrastive|USCL]] 進一步利用掃查視訊的天然時序連續性進行對比預訓練，大幅降低對人工標註的依賴。

### 2.3 從「孤立小模型」邁向「通用基礎模型 (US-FM)」
- **過去**：在單一中心小型資料集（如 [[busi_dataset|BUSI]]）訓練的模型，移植至其他醫院或掌上型探頭時性能嚴重退化。
- **演進**：[[lin2023_samus|SAMUS]] 與 [[wang2024_ultrasound_foundation_survey|超音波基礎模型]] 透過參數高效微調（PEFT），將自然影像大模型的拓撲世界知識與超音波特異性邊緣融合，邁向跨器官、跨機型的通用多功能智慧代理。

---

## 3. 結語與未來研究前沿
超音波 AI 的終極形態將是整合了**波束成形物理前端、時空動態視訊理解、視覺-語言即時臨床引導**的智慧伴侶系統，特別是在床邊掌上超音波（POCUS）普及化與基層醫療賦能方面，將發揮不可替代的臨床價值。
