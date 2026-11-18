---
title: "深部微血管超解析度顯微造影 (Super-Resolution Microvascular Imaging)"
aliases: ["Microvascular Imaging", "ULM Vascular Reconstruction", "微血管造影"]
category: "task"
tags: ["super-resolution", "vascular", "microcirculation", "angiogenesis", "ulm"]
last_updated: "2026-11-17"
sources: ["[[errico2015_ulm_super_resolution]]"]
---

# 深部微血管超解析度顯微造影

## 1. 臨床與科學研究背景
人體大腦微血管網、腫瘤新生血管（Tumor Neoangiogenesis）、腎小球微循環的管徑通常介於 $5$ 至 $30\,\mu\text{m}$。
在過去，活體深部組織微循環的觀測一直存在技術斷層：
- **光學雙光子顯微鏡**：解析度高達亞微米，但光子被人體組織強烈散射，成像深度被死鎖在皮膚或腦皮層下 $500\,\mu\text{m}$ 處；
- **傳統超音波都卜勒 (Doppler)**：穿透深，但受限於聲波波長繞射極限（$\sim 200\,\mu\text{m}$），只能觀測直徑大於幾百微米的大動脈與大靜脈，且極易受組織跳動雜波干擾。

---

## 2. ULM 超解析度造影的技術實現
基於 [[errico2015_ulm_super_resolution|Errico et al. (Nature 2015)]] 提出的 [[ultrasound_super_resolution|超快超音波定位顯微術 (ULM)]]：
1. **超快平面波採集**：探頭以數千赫茲（$1,000-10,000\,\text{Hz}$）發射無聚焦平面波；
2. **時空 SVD 濾波**：在空間-時間矩陣上執行奇異值分解，剝離慢速跳動的組織信號，只保留血管內微氣泡的都卜勒頻移；
3. **質心亞像素超定位**：利用 2D 高斯擬合定位每個微氣泡，累計數萬幀重建出如星系般精緻的活體深腦血管床圖譜。

---

## 3. 臨床應用價值
- **早期腫瘤微血管特徵識別**：腫瘤血管通常具有扭曲、擴張與分叉異常的病態結構，ULM 能在腫瘤尚處於毫米級時檢測出新生毛細血管網。
- **腦血管疾病與中風評估**：無創穿透顱骨直接繪製大腦穿通動脈血流速度與阻力指數。

---

## 4. 關聯頁面 (Wiki Links)
- **概念專題**：[[ultrasound_super_resolution|超音波超解析度成像原理]]
- **前沿研究**：[[errico2015_ulm_super_resolution|ULM Nature 論文精讀]]
- **訊號處理前端**：[[beamforming_physics|波束成形與點擴散函數 (PSF)]]
