---
title: "HC18: 產前超音波胎兒頭圍自動測量國際挑戰賽資料集"
aliases: ["HC18 Dataset", "HC18 Grand Challenge", "Fetal Head Ultrasound Dataset"]
category: "dataset"
tags: ["dataset", "obstetrics", "fetal-biometry", "head-circumference", "grand-challenge"]
last_updated: "2026-11-17"
sources: ["[[vandenheuvel2018_hc18]]"]
---

# HC18 資料集 (Fetal Head Circumference Grand Challenge)

## 1. 資料集概況與發起背景
- **釋出年份**：2018 年（[[vandenheuvel2018_hc18|van den Heuvel et al.]]）
- **發起機構**：荷蘭拉德堡德大學醫學中心（Radboud University Medical Center）
- **受試者與影像規模**：採集自 751 位孕婦，共計 1,334 張 2D 超音波切面影像。
  - **訓練集**：999 張（公開原始影像與專家手繪橢圓標註）。
  - **測試集**：335 張（僅公開影像，線上隱藏評測）。
- **孕期覆蓋**：完整涵蓋妊娠早期（First Trimester）、中期（Second Trimester）及晚期（Third Trimester）。

---

## 2. 標註規格與臨床評測指標
### 2.1 金標準格式
由資深產科超音波專科醫師依據臨床標準（丘腦水平橫切面）手動標註胎兒顱骨外緣的幾何橢圓參數：
- 橢圓幾何中心坐標 $(x_0, y_0)$；
- 橢圓長半軸 $a$ 與短半軸 $b$；
- 橢圓旋轉角度 $\alpha$。

### 2.2 評測指標
1. **頭圍絕對差異 (Difference in HC, mm)**：
   $$\Delta \text{HC} = |\text{HC}_{\text{pred}} - \text{HC}_{\text{true}}|$$
2. **Dice 相似係數 (DSC)**：評估橢圓覆蓋面積的空間重疊率。
3. **豪斯多夫距離 (Hausdorff Distance, HD)**：度量預測顱骨輪廓與真實輪廓的最大幾何偏差。

---

## 3. 面臨的聲學挑戰與演算法價值
胎兒頭部受母體羊水混響、母體骨盆以及胎兒自身骨骼之[[acoustic_shadowing|聲影]]影響，邊緣常有 20-40% 處於聲學缺失狀態。HC18 成為檢驗神經網路結合幾何形狀先驗（如橢圓擬合約束）的經典黃金標準。

---

## 4. 關聯頁面 (Wiki Links)
- **原始論文解析**：[[vandenheuvel2018_hc18|HC18 論文精讀]]
- **臨床任務**：[[fetal_biometry_measurement|胎兒產前生物測量任務]]
- **聲學現象**：[[acoustic_shadowing|聲影效應]]
- **基礎演算法**：[[unet_architecture|U-Net 卷積分割]]
