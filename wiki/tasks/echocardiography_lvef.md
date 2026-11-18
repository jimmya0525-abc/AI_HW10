---
title: "超音波心動圖多結構分割與左心室射血分數 (LVEF) 評估"
aliases: ["Echocardiography LVEF", "心臟超音波", "射血分數定量", "Simpson's Biplane"]
category: "task"
tags: ["cardiac", "echocardiography", "lvef", "hemodynamics", "segmentation"]
last_updated: "2026-11-17"
sources: ["[[leclerc2019_camus]]", "[[ouyang2020_echonet_dynamic]]"]
---

# 超音波心動圖與左心室射血分數 (LVEF) 定量評估

## 1. 臨床意義：心臟血流動力學的核心指標
超音波心動圖（Echocardiography）是全球最普及的心臟非侵入式診斷工具。
其中，**左心室射血分數 (Left Ventricular Ejection Fraction, LVEF)** 是衡量心臟幫浦功能的最關鍵臨床指標：
$$\text{LVEF} = \frac{\text{EDV} - \text{ESV}}{\text{EDV}} \times 100\%$$
- **臨床標準分級**：
  - $\ge 50\%$：正常射血功能。
  - $40-49\%$：輕度降低（HFmrEF）。
  - $< 40\%$：顯著降低，確診射血分數降低型心臟衰竭（HFrEF），需緊急臨床介入。

---

## 2. 臨床測量標準：雙平面辛普森法 (Simpson's Biplane Method)
臨床指南（ASE / EACVI）推薦在**心尖四腔心（A4C）**與**心尖雙腔心（A2C）**兩個切面上，於**舒張末期（ED）**與**收縮末期（ES）**手動勾勒左心室心內膜邊緣。系統將心室縱軸沿線切割為 20 個厚度均勻的圓柱體圓盤進行幾何積分求和算出容積：
$$V = \frac{\pi}{4} \sum_{i=1}^{20} a_i \cdot b_i \cdot h$$
人工手動勾勒極其耗時，且高度依賴醫師資歷，觀察者間變異（Inter-observer variability）通常高達 5-10%。

---

## 3. 人工智慧發展路徑與代表成果
1. **靜態幀解剖分割範式 (Static Multi-structure Segmentation)**：
   - 代表：[[camus_dataset|CAMUS 基準]]（[[leclerc2019_camus|Leclerc et al. 2019]]）。
   - 採用 [[unet_architecture|U-Net]] 同時精確分割左心室腔、心肌層與左心房，將 LVEF 估算誤差壓低至 5% 以內。
2. **端到端時空動態視訊範式 (Dynamic Video-based Deep Learning)**：
   - 代表：[[echonet_dynamic_dataset|EchoNet-Dynamic]]（[[ouyang2020_echonet_dynamic|Ouyang et al. Nature 2020]]）。
   - 捨棄人工手動指定 ED/ES 幀，採用 R(2+1)D 卷積神經網路直接消化長時連續心動動態視訊，逐心搏輸出 LVEF 與心衰竭預測，檢出心衰竭 AUC 高達 0.97。

---

## 4. 關聯頁面 (Wiki Links)
- **代表資料集**：[[camus_dataset|CAMUS 心臟超音波資料集]]、[[echonet_dynamic_dataset|EchoNet-Dynamic 視訊資料集]]
- **核心架構**：[[echonet_spatiotemporal|EchoNet 時空視訊模型]]、[[unet_architecture|U-Net 心臟分割]]
- **論文解析**：[[leclerc2019_camus|CAMUS 論文]]、[[ouyang2020_echonet_dynamic|EchoNet Nature 論文]]
