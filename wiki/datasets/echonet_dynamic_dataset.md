---
title: "EchoNet-Dynamic: 萬例超音波心動圖視訊基準資料庫"
aliases: ["EchoNet-Dynamic Dataset", "EchoNet", "Stanford Echo Database"]
category: "dataset"
tags: ["dataset", "cardiac", "video-dataset", "lvef", "echocardiography", "nature"]
last_updated: "2026-11-17"
sources: ["[[ouyang2020_echonet_dynamic]]"]
---

# EchoNet-Dynamic 資料庫

## 1. 資料庫規模與劃時代突破
- **釋出年份**：2020 年（[[ouyang2020_echonet_dynamic|Ouyang et al. Nature]]）
- **發起機構**：史丹佛大學醫學院（Stanford University School of Medicine）
- **視訊總量**：**10,030 支完整超音波心動圖動態視訊（Cine-loops）**
- **標註形式**：涵蓋上萬名患者由執業心臟專科醫師審核之臨床射血分數（LVEF）、收縮/舒張期容積數值，並提供數萬幀心內膜輪廓幾何座標。

---

## 2. 視訊數據特徵規格
- **掃查切面**：標準心尖四腔心視角（Apical 4-Chamber, A4C）。
- **時序長度**：每支視訊包含多個完整心搏週期（通常為 32 至 112 幀，採樣率約 50 fps）。
- **臨床表型涵蓋**：包含正常心臟、擴張型心肌病、缺血性心臟病、心肌肥厚及射血分數低下型心臟衰竭（HFrEF）。

---

## 3. 在 AI 與超音波領域的基準地位
以往醫學超音波公開資料集規模通常僅數百例靜態圖片（如 [[busi_dataset|BUSI]]、[[camus_dataset|CAMUS]]），容易導致深度模型過擬合。
EchoNet-Dynamic 是超音波領域首個達到萬例級別的**動態視訊大數據集**，徹底釋放了時空深度學習（如 3D-CNN、[[echonet_spatiotemporal|R(2+1)D]]）的潛力，並成為驗證超音波時序自監督學習模型的重要基礎設施。

---

## 4. 關聯頁面 (Wiki Links)
- **原始論文解析**：[[ouyang2020_echonet_dynamic|EchoNet-Dynamic Nature 論文]]
- **專屬模型架構**：[[echonet_spatiotemporal|EchoNet 時空深度學習架構]]
- **臨床任務**：[[echocardiography_lvef|心臟超音波射血分數定量評估]]
