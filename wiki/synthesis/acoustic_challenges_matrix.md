---
title: "超音波聲學物理限制與 AI 演算法因應對策矩陣"
aliases: ["Acoustic Challenges Matrix", "聲學挑戰對策矩陣", "超音波偽影與 AI"]
category: "synthesis"
tags: ["synthesis", "matrix", "physics", "artifacts", "challenges"]
last_updated: "2026-11-17"
sources: [
  "[[ronneberger2015_unet]]",
  "[[aldhabyani2020_busi]]",
  "[[leclerc2019_camus]]",
  "[[lin2023_samus]]",
  "[[vandenheuvel2018_hc18]]",
  "[[errico2015_ulm_super_resolution]]",
  "[[luchies2018_dnn_beamforming]]",
  "[[jiao2020_uscl_contrastive]]"
]
---

# 超音波聲學物理限制與 AI 演算法因應對策矩陣

## 1. 綜述視角
與 X 光、電腦斷層（CT）或磁振造影（MRI）相比，超音波影像具有最特殊的波動聲學與介質干涉特性。許多在常規自然電腦視覺（CV）中表現出色的模型，在超音波領域遭遇嚴重水土不服。
本頁面梳理超音波六大核心聲學物理限制，並對比古典方法與現代 AI 演算法的因應對策：

---

## 2. 聲學物理限制 vs AI 應對矩陣

| 聲學物理現象 | 物理產生機制與臨床表徵 | 對常規演算法的破壞 | 現代 AI / 深度學習因應架構 | 代表文獻與實體頁面 |
| :--- | :--- | :--- | :--- | :--- |
| **[[speckle_noise\|斑點噪聲 (Speckle Noise)]]** | 亞波長微散射子同調干涉，在包絡檢波後呈現乘性瑞利分佈顆粒感 | 降低訊噪比與對比度，造成假性邊界，干擾自然大模型 (SAM) | ① [[deep_beamforming\|DNN 前端波束成形]]：直接在 RF 域消除旁瓣；<br>② [[ultrasound_contrastive_learning\|USCL 聲學增強]]：注入斑點噪聲強迫模型學習結構不變性 | [[luchies2018_dnn_beamforming\|Luchies 2018]]<br>[[jiao2020_uscl_contrastive\|Jiao 2020]] |
| **[[acoustic_shadowing\|後方聲影 (Shadowing)]]** | 惡性腫瘤微鈣化或緻密骨骼造成聲波指數級高衰減，深部回聲消失 | 輪廓後壁中斷（Dropout），主動輪廓模型與邊緣檢測法無法閉合邊界 | ① [[samus_adapter\|SAMUS 全局注意力]]：利用全局拓撲推斷缺失邊緣；<br>② 幾何形狀先驗約束（如橢圓擬合） | [[aldhabyani2020_busi\|Al-Dhabyani 2020]]<br>[[vandenheuvel2018_hc18\|van den Heuvel 2018]] |
| **側向聲影與折射脫落** | 聲束在曲面囊腫或骨壁切向入射，發生全反射與臨界角折射 | 心臟心尖側壁或胎兒頭骨兩側出現狹長黑條帶暗區 | ① [[unet_architecture\|U-Net 跳躍連接]]：拼接淺層邊界高頻特徵；<br>② [[hc18_dataset\|HC18 幾何橢圓擬合]]：強制拓撲封閉 | [[ronneberger2015_unet\|Ronneberger 2015]]<br>[[leclerc2019_camus\|Leclerc 2019]] |
| **波動繞射極限** | 聲學波動傳播受限於波長 $\lambda$ 與孔徑尺寸，微米級微血管無法辨析 | 無法觀察早期腫瘤新生血管與深腦微循環 | [[ultrasound_super_resolution\|ULM 超快定位顯微術]]：藉由微氣泡點擴散函數（PSF）質心超定位，突破繞射極限十倍以上 | [[errico2015_ulm_super_resolution\|Errico 2015 (Nature)]] |
| **聲速非均勻性與像差** | 脂肪 ($1450\,\text{m/s}$) 與肌肉 ($1580\,\text{m/s}$) 聲速不一致，造成幾何飛行時間延遲失準 | 傳統延遲相加（DAS）產生破壞性干涉，波束散焦且側向解析度大跌 | [[deep_beamforming\|深度學習 RF 訊號映射]]：神經網路直接學習非均勻介質中的非線性聚焦校正 | [[luchies2018_dnn_beamforming\|Luchies 2018]] |
| **時序動態主觀性** | 傳統超音波心動圖僅選取單一靜態收縮/舒張幀，人為判定誤差高達 10% | 忽略心肌連續收縮加速度與瓣膜開閉動態血流特徵 | [[echonet_spatiotemporal\|EchoNet R(2+1)D 時空視訊卷積]]：直接輸入連續視訊，自動進行 beat-to-beat 容積回歸 | [[ouyang2020_echonet_dynamic\|Ouyang 2020 (Nature)]] |

---

## 3. 跨頁面交叉導航
- **核心概念匯流**：[[speckle_noise|斑點噪聲]]、[[acoustic_shadowing|聲影效應]]、[[beamforming_physics|波束成形物理]]、[[ultrasound_super_resolution|超解析度顯微成像]]
- **方法演算法匯流**：[[unet_architecture|U-Net]]、[[samus_adapter|SAMUS]]、[[echonet_spatiotemporal|EchoNet]]、[[deep_beamforming|深度波束成形]]、[[ultrasound_contrastive_learning|USCL 對比學習]]
- **歷史脈絡導航**：[[ultrasound_ai_evolution|超音波 AI 技術演進史]]
