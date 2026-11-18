---
title: "CAMUS: 二維超音波心動圖多結構分割臨床基準資料集"
aliases: ["CAMUS Dataset", "CAMUS Benchmark", "Cardiac Acquisitions for Multi-structure Ultrasound Segmentation"]
category: "dataset"
tags: ["dataset", "cardiac", "echocardiography", "segmentation", "lvef", "camus"]
last_updated: "2026-11-17"
sources: ["[[leclerc2019_camus]]"]
---

# CAMUS 資料集 (Cardiac Acquisitions for Multi-structure Ultrasound Segmentation)

## 1. 資料集規格與採集背景
- **釋出年份**：2019 年（[[leclerc2019_camus|Leclerc et al.]]）
- **發起機構**：法國 CREATIS 實驗室與挪威 SINTEF
- **病患規模**：500 名臨床連續就診患者（涵蓋正常、缺血性心臟病與各級心衰竭）
- **切面標準**：標準心尖四腔心（A4C）與心尖雙腔心（A2C）
- **關鍵心動時相**：舒張末期（End-Diastole, ED）與收縮末期（End-Systole, ES）

---

## 2. 標註解剖目標與聲學視窗品質分級
### 2.1 標註目標
1. **左心室內膜腔 (Left Ventricle Cavity, LV)**
2. **左心室心肌壁 (Myocardium, MYO)**
3. **左心房內膜腔 (Left Atrium Cavity, LA)**

### 2.2 聲學視窗品質分級 (Image Quality Stratification)
CAMUS 依臨床真實聲學條件，將 500 位病患嚴格區分為三級：
- **Good (良好視窗)**：心內膜與心外膜界面清晰完整。
- **Medium (中等視窗)**：局部存在斑點雜訊或邊界模糊。
- **Poor (惡劣視窗)**：存在嚴重的側壁聲學脫落（Lateral Acoustic Dropout）或肋骨陰影遮擋。

---

## 3. 臨床診斷指標推導
CAMUS 的最終目標是驗證 AI 自動計算臨床血流動力學指標的可行性：
- 透過分割結果直接推導左心室舒張末容積（EDV）、收縮末容積（ESV）。
- 利用雙平面辛普森法計算射血分數（LVEF）：
  $$\text{LVEF} = \frac{\text{EDV} - \text{ESV}}{\text{EDV}} \times 100\%$$
- 臨床結論：最優深度學習模型與心臟科專家標註之 LVEF 相關係數高達 0.95，絕對誤差 $<5\%$。

---

## 4. 關聯頁面 (Wiki Links)
- **原始論文解析**：[[leclerc2019_camus|CAMUS 論文精讀]]
- **臨床任務**：[[echocardiography_lvef|心臟超音波結構分割與射血分數定量]]
- **對比視訊資料庫**：[[echonet_dynamic_dataset|EchoNet-Dynamic 視訊資料集]]
- **基準演算法**：[[unet_architecture|U-Net 心臟分割]]、[[samus_adapter|SAMUS 大模型表現]]
