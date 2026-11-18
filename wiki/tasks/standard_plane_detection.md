---
title: "超音波標準切面辨識與即時掃查品質控制 (Standard Plane Detection)"
aliases: ["Standard Plane Detection", "超音波標準切面", "POCUS 智能導引", "切面質控"]
category: "task"
tags: ["quality-control", "standard-plane", "pocus", "classification", "workflow"]
last_updated: "2026-11-17"
sources: ["[[jiao2020_uscl_contrastive]]", "[[vandenheuvel2018_hc18]]", "[[wang2024_ultrasound_foundation_survey]]"]
---

# 超音波標準切面辨識與即時掃查品質控制

## 1. 臨床痛點：強烈的人員依賴性
超音波是一門「操作者依賴性（Operator-dependent）」極高的檢查技術。超音波技師或醫師必須以手法自由滑動、旋轉、傾斜手持探頭：
- **切面標準度直接決定診斷正確性**：若探頭切面角度偏移 5 度，測量出的胎兒頭圍或心室射血分數將完全失真。
- **基層與急診醫療瓶頸**：在急診（ER）、重症病房（ICU）或偏鄉進行床邊掌上超音波（Point-of-Care Ultrasound, POCUS）時，缺乏資深超音波醫師，非專業人員極難迅速找到規範切面。

---

## 2. AI 解決方案與工作流
1. **即時切面分類與目標檢測**：
   在掃查視訊串流中，以高於 30 fps 的速度即時檢測畫面是否符合臨床指南標準（如產前超音波的丘腦切面、心室流出道切面、腹圍切面，或心臟的 A4C、PLAX 切面）。
2. **解剖關鍵標誌即時反饋 (Quality Assessment)**：
   檢測切面內是否同時出現必備解剖結構（例如頭圍測量時必須出現的透明隔腔 CSP 與大腦鐮）。
3. **探頭導引指示 (Probe Guidance)**：
   分析當前非標準切面與標準切面間的幾何空間變換，在螢幕上即時提示操作者：「請將探頭向左傾斜 5 度」或「請輕微順時針旋轉」。

---

## 3. 預訓練與基礎模型賦能
如 [[jiao2020_uscl_contrastive|USCL]] 與 [[wang2024_ultrasound_foundation_survey|Wang et al. (2024)]] 所述，利用未標註的超音波掃查視訊進行自監督時序預訓練，能讓模型深刻理解探頭掃查視角連續切換時的解剖過渡特徵，大幅降低在基層醫療場景中的標準切面辨識誤判率。

---

## 4. 關聯頁面 (Wiki Links)
- **基礎架構**：[[ultrasound_contrastive_learning|超音波自監督對比學習]]
- **下游測量**：[[fetal_biometry_measurement|胎兒產前測量任務]]
- **綜述文獻**：[[wang2024_ultrasound_foundation_survey|超音波大模型綜述]]
