---
title: "聲學聲影 (Acoustic Shadowing) 與增強效應"
aliases: ["Acoustic Shadowing", "後方聲影", "後方回聲增強", "聲學偽影"]
category: "concept"
tags: ["physics", "acoustics", "artifact", "clinical-marker"]
last_updated: "2026-11-17"
sources: ["[[aldhabyani2020_busi]]", "[[vandenheuvel2018_hc18]]", "[[wang2024_ultrasound_foundation_survey]]"]
---

# 聲影效應 (Acoustic Shadowing)

## 1. 物理衰減機制與定義
**聲學聲影（Acoustic Shadowing）**是超音波穿透介質時，因強烈聲阻抗失配、全反射或超高衰減係數，導致深部組織接收不到聲波能量而形成的暗區（低回聲或無回聲帶）。
- **衰減定律**：超音波能量隨深度 $z$ 指數衰減：
  $$I(z) = I_0 \cdot \exp(-2\alpha f z)$$
  其中 $\alpha$ 為組織衰減係數（$\text{dB}/(\text{cm}\cdot\text{MHz})$），$f$ 為探頭中心頻率。
- **高衰減結構**：骨骼、鈣化結節、膽結石、緻密纖維腫瘤具有極高衰減值，其後方產生顯著的暗黑帶。

---

## 2. 臨床病理診斷價值
在臨床超音波影像中，聲影與其對應的後方增強效應是鑑別良惡性腫瘤的核心 BI-RADS 診斷標準：
1. **後方聲影（Posterior Acoustic Shadowing）**：
   - 常見於**惡性乳腺腫瘤**（如浸潤性導管癌，見 [[busi_dataset|BUSI 資料集]]）或胎兒高密度顱骨骨骼（見 [[hc18_dataset|HC18 資料集]]）。
   - 惡性病灶內部纖維增生反應及微鈣化強烈吸收並散射聲波，在其後方投射出深色聲影。
2. **後方回聲增強（Posterior Acoustic Enhancement）**：
   - 常見於**良性囊腫（Cysts）**。液體（囊液、尿液、血液）衰減極低，通過囊體後的聲能遠高於周圍實質組織，導致後方組織亮度顯著高於兩側。

---

## 3. 對電腦視覺與深度學習模型的挑戰
- **邊緣中斷（Edge Dropout）**：聲影造成病灶後壁與深層正常組織界面完全失去回聲對比，導致傳統基於梯度或邊緣檢測的模型（如主動輪廓模型 Snake）無法封閉輪廓。
- **神經網路的應對範式**：
  - **形狀幾何先驗**：如 [[hc18_dataset|HC18]] 中透過橢圓擬合（Ellipse Fitting）強制恢復顱骨被聲影截斷的拓撲形狀。
  - **全局上下文注意力**：[[samus_adapter|SAMUS]] 與 Transformer 架構藉由全局自注意力機制，利用病灶兩側的空間先驗推斷後壁模糊區域的幾何邊界。

---

## 4. 關聯頁面 (Wiki Links)
- **臨床任務**：[[breast_lesion_segmentation|乳腺結節良惡性分割]]、[[fetal_biometry_measurement|胎兒產前測量]]
- **對應資料集**：[[busi_dataset|BUSI 資料集]]、[[hc18_dataset|HC18 資料集]]
- **干擾對比**：[[speckle_noise|斑點噪聲 (Speckle Noise)]]
