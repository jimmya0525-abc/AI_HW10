---
title: "超音波超解析度顯微成像 (Ultrasound Localization Microscopy, ULM)"
aliases: ["ULM", "Ultrasound Super-Resolution", "超解析度造影", "微氣泡定位"]
category: "concept"
tags: ["physics", "super-resolution", "microbubbles", "optics-analogy", "diffraction-limit"]
last_updated: "2026-11-17"
sources: ["[[errico2015_ulm_super_resolution]]"]
---

# 超音波超解析度顯微成像 (ULM)

## 1. 繞射極限的百年困局
在經典波動聲學中，超音波影像的解析度遵循波動繞射理論（Rayleigh / Abbe 準則）：
$$\text{Resolution} \approx 1.22 \frac{c \cdot z}{f_0 \cdot D}$$
- **穿透深度與解析度的矛盾**：
  - 高頻超音波（例如 $30-50\,\text{MHz}$）波長短、解析度高，但在生物組織中衰減極其劇烈，穿透深度僅數毫米。
  - 低頻超音波（例如 $1-5\,\text{MHz}$）穿透深度可達數十公分，但波長長達數百微米，根本無法分辨直徑僅 $5-10\,\mu\text{m}$ 的毛細微血管網。

---

## 2. ULM 的運作原理：借鑑光學單分子定位
2015 年，[[errico2015_ulm_super_resolution|Errico et al.]] 在《Nature》提出超快超音波定位顯微術（ULM），將光學超解析度（PALM/STORM）的單分子閃爍定位哲學移植至聲學領域：
1. **靜脈注射微氣泡（Microbubbles）**：直徑 $1-3\,\mu\text{m}$ 的氣體微球作為血管內的強單點散射子。
2. **時空雜波過濾（SVD Clutter Filter）**：消除體內呼吸與搏動引起的組織回聲，僅分離出運動氣泡。
3. **亞像素微氣泡質心定位（Sub-pixel Localization）**：
   單個微氣泡回聲即為成像系統的點擴散函數（PSF）。只要氣泡分佈足夠稀疏，透過 2D 雙二維高斯函數擬合：
   $$\hat{I}(x, y) = A \cdot \exp\left( - \frac{(x - x_0)^2 + (y - y_0)^2}{2\sigma^2} \right) + B$$
   即可精確找出氣泡幾何中心 $(x_0, y_0)$，定位精度達到微米級（$\sim 10\,\mu\text{m}$），完全脫離了波長 $\lambda$ 的尺度束縛。
4. **軌跡追蹤與流速測量**：連續幀追蹤微氣泡生成血液流速向量圖。

---

## 3. 現代 AI 在 ULM 中的核心賦能
- **高密度氣泡解耦**：傳統 ULM 依賴稀疏氣泡，需數千至數萬幀數據累積，耗時長且易受病患位移影響。深度神經網路（如 Deep-ULM）能夠直接分解互相重疊的複雜多氣泡干涉波形，使影像採集時間縮短 10 到 100 倍。
- **神經流場重建**：結合神經輻射場（NeRF）與隱式神經表示（INR），直接從不連續軌跡插值出血流動力學參數。

---

## 4. 關聯頁面 (Wiki Links)
- **奠基文獻**：[[errico2015_ulm_super_resolution|Errico et al. 2015 Nature 論文解析]]
- **聲學概念**：[[beamforming_physics|波束成形與點擴散函數 (PSF)]]
- **臨床任務**：[[super_resolution_vascular_imaging|深部微血管超解析度造影任務]]
