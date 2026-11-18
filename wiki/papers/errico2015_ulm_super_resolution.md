---
title: "ULM: 超快超音波定位顯微鏡突破繞射極限 (Errico et al., 2015)"
aliases: ["ULM", "Errico 2015", "Ultrasound Super-Resolution"]
category: "paper"
tags: ["ultrasound", "super-resolution", "physics", "microbubbles", "nature-paper"]
last_updated: "2026-11-17"
sources: ["[[raw/papers/07_errico2015_ulm_super_resolution.md]]"]
---

# Ultrafast Ultrasound Localization Microscopy for Deep Super-Resolution Vascular Imaging (ULM)

- **作者**：Claudia Errico, Juliette Pierre, Olivier Couture, Mickael Tanter 等
- **發表場合**：Nature 527, 499–502 (2015)
- **原始文獻依據**：[[raw/papers/07_errico2015_ulm_super_resolution.md]]

---

## 1. 論文核心貢獻
本文發表於《Nature》，在醫學物理學上實現了歷史性突破：**成功打破了波動聲學百年來的繞射極限（Diffraction Limit）**。透過借鑑光學超級解析度顯微技術（PALM/STORM）的單分子定位概念，團隊結合超快平面波成像（Ultrafast Plane-Wave Imaging, $>1,000$ fps）與靜脈注射微氣泡對比劑（Microbubbles），在活體大腦深處實現了空間解析度高達 $10\,\mu\text{m}$ 的微血管超解析度顯微成像（提升超過一個數量級）。

---

## 2. 聲學物理機制與定位演算法
1. **聲學繞射極限**：
   依據阿貝準則（Abbe limit），超音波側向解析度受限於波長 $\lambda$：
   $$R \approx 1.22 \frac{c \cdot z}{f_0 \cdot D}$$
   傳統 15 MHz 探頭波長約 $100\,\mu\text{m}$，無法辨析人體內徑僅 $5-10\,\mu\text{m}$ 的毛細微血管。
2. **單點散射子超定位 (Super-Localization)**：
   微氣泡直徑僅 $1-3\,\mu\text{m}$，其回波本質上為成像系統的點擴散函數（Point Spread Function, PSF）。只要控制氣泡濃度使其稀疏分佈，即可透過 2D 高斯擬合找出其質心幾何中心，定位精度可達亞微米級。
3. **時空雜波過濾 (SVD Clutter Filtering)**：
   利用奇異值分解（SVD）分離緩慢蠕動的組織背景與高速流動的血管內微氣泡信號。

---

## 3. 與 AI / 深度學習的結合演進
在傳統 ULM 中，為了防止氣泡回波 PSF 空間重疊，必須將微氣泡濃度降到極低，導致完整重構一張微血管圖需累積數萬幀（耗時數分鐘），容易受到病患呼吸運動影響。
後續深度學習研究（如 Deep-ULM、ULM-Net）利用卷積網路直接解耦高密度重疊 PSF，使 ULM 重構成像速度提升 10 至 100 倍。

---

## 4. 關聯頁面 (Wiki Links)
- **概念專題**：[[ultrasound_super_resolution|超音波超解析度成像原理]]
- **聲學物理**：[[beamforming_physics|波束成形與點擴散函數 (PSF)]]
- **臨床任務**：[[super_resolution_vascular_imaging|深部微血管超解析度造影]]
