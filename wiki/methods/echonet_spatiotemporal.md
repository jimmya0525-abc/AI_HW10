---
title: "EchoNet 時空視訊深度學習架構"
aliases: ["EchoNet Architecture", "R(2+1)D Ultrasound", "Video-based Echocardiography"]
category: "method"
tags: ["video-dl", "cardiac", "3d-cnn", "echocardiography", "lvef"]
last_updated: "2026-11-17"
sources: ["[[ouyang2020_echonet_dynamic]]", "[[leclerc2019_camus]]"]
---

# EchoNet 時空視訊深度學習架構

## 1. 核心突破：從靜態幀到連續心搏視訊
在過去的超音波心動圖研究（如 [[camus_dataset|CAMUS]]）中，臨床醫師與演算法皆聚焦於心動週期中的特定單幀：舒張末期（ED）與收縮末期（ES）。
然而，這種靜態分析面臨兩大弊端：
1. **選幀的主觀變異性**：不同醫師對「最大/最小心室容積幀」的判斷往往相差 1-3 幀，直接造成射血分數計算誤差。
2. **忽略血流動力學連續過程**：心肌的協同收縮、二尖瓣啟閉以及局部壁運動異常（Wall Motion Abnormality）本質上是高訊框率（30-60 fps）的動態物理過程。

[[ouyang2020_echonet_dynamic|Ouyang et al. (Nature 2020)]] 提出的 **EchoNet-Dynamic** 首次建立了完整的端到端視訊級分析管道。

---

## 2. 時空卷積解耦架構：R(2+1)D
標準 3D 卷積在處理醫學影像時計算代價極高且極易過擬合。EchoNet-Dynamic 採用了 **R(2+1)D** 架構，將一個 $k_t \times k_s \times k_s$ 的 3D 卷積分解為兩步：
1. **空間卷積 (Spatial Conv, $1 \times k_s \times k_s$)**：在單一幀內提取心室幾何形狀與組織界面邊緣；
2. **非線性激活 (ReLU)**：增加非線性容量；
3. **時間卷積 (Temporal Conv, $k_t \times 1 \times 1$)**：在相鄰時間軸上關聯特徵響應，捕捉心肌舒縮加速度。

```
輸入連續超音波視訊 (B x C x T x H x W)
                │
                ▼
        [空間 2D 卷積 (1 x 3 x 3)] ──> 提取解剖邊界特徵
                │
                ▼
            [ReLU 激活]
                │
                ▼
        [時間 1D 卷積 (3 x 1 x 1)] ──> 提取時間動態血流特徵
                │
                ▼
      [特徵池化與多任務分支輸出]
        ├── 逐幀心內膜輪廓 (Semantic Masks)
        └── 連續射血分數回歸 (LVEF Regression)
```

---

## 3. 多任務學習與臨床轉化
模型透過多任務並行訓練：
- **分割分支**：弱監督學習心室腔在多個心動週期內的連續二維截面積變化曲線 $A(t)$；
- **回歸分支**：直接將高維時空特徵向量映射為左心室舒張末期容積（EDV）、收縮末期容積（ESV）及射血分數（LVEF）：
  $$\text{LVEF} = \frac{\text{EDV} - \text{ESV}}{\text{EDV}} \times 100\%$$
- 絕對預測誤差僅 4.1%，展現了時序資訊抗噪的巨大優勢。

---

## 4. 關聯頁面 (Wiki Links)
- **原始文獻**：[[ouyang2020_echonet_dynamic|EchoNet-Dynamic 論文解析]]
- **實體資料集**：[[echonet_dynamic_dataset|EchoNet-Dynamic 資料庫]]
- **臨床任務**：[[echocardiography_lvef|心臟超音波射血分數定量評估]]
- **靜態比較**：[[leclerc2019_camus|CAMUS 二維靜態基準]]
