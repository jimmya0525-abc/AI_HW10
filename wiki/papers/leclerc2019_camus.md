---
title: "CAMUS: 二維超音波心動圖多結構分割基準 (Leclerc et al., 2019)"
aliases: ["CAMUS", "Leclerc 2019"]
category: "paper"
tags: ["ultrasound", "cardiac", "echocardiography", "segmentation", "lvef"]
last_updated: "2026-11-17"
sources: ["[[raw/papers/03_leclerc2019_camus.md]]"]
---

# Deep Learning for Segmentation Using an Open Large-Scale Dataset in 2D Echocardiography (CAMUS)

- **作者**：Sarah Leclerc, Erik Smistad, Joao Pedrosa, Olivier Bernard 等
- **發表場合**：IEEE Transactions on Medical Imaging (TMI), 2019
- **原始文獻依據**：[[raw/papers/03_leclerc2019_camus.md]]

---

## 1. 論文核心貢獻
本文釋出了心臟超音波領域極具影響力的標準臨床公開資料集 **CAMUS**（500 位病患二維超音波心動圖），並建立了一套涵蓋心室腔心內膜（Endocardium）、心肌層（Myocardium）及左心房（Left Atrium）的多結構分割深度學習基準，驗證了 AI 自動計算心臟射血分數（LVEF）與心肌應變（Strain）已達到心臟專科醫師臨床觀察者間差異水平。

---

## 2. 資料集臨床特徵與影像視角
- **視角設定**：嚴格涵蓋心尖雙腔心（Apical 2-Chamber, A2C）與心尖四腔心（Apical 4-Chamber, A4C）。
- **關鍵心動時相**：標註收縮末期（End-Systole, ES）與舒張末期（End-Diastole, ED）。
- **聲學視窗分級**：分為優良（Good）、中等（Medium）與惡劣（Poor），如實反映超音波受肋骨遮擋與肥胖病患造成的聲學失真。

---

## 3. 實驗發現與臨床指標轉化
1. **結構分割指標**：深度學習模型在優良視窗下 Dice 可達 0.92（左心室腔）與 0.88（心肌），但在惡劣聲學視窗中，由於心尖側壁聲學信號脫落（Acoustic Dropout），Dice 下降 6-10%。
2. **射血分數 (LVEF) 臨床轉化**：
   利用雙平面辛普森法（Biplane Simpson's Rule），模型推算 LVEF 的絕對誤差控制在 5.0% 以內，證明幾何語意分割可無縫串接臨床心臟血流動力學診斷。

---

## 4. 關聯頁面 (Wiki Links)
- **實體資料集**：[[camus_dataset|CAMUS 心臟超音波資料集]]
- **臨床任務**：[[echocardiography_lvef|超音波心動圖與心臟功能定量分析 (LVEF)]]
- **演進對比**：[[ouyang2020_echonet_dynamic|EchoNet-Dynamic 視訊心動圖]]
- **基礎模型測試**：[[samus_adapter|SAMUS 在心臟領域的泛化表現]]
