---
title: "超音波基礎模型綜述與多中心標竿評測 (Wang et al., 2024)"
aliases: ["US Foundation Survey", "Wang 2024"]
category: "paper"
tags: ["ultrasound", "foundation-model", "survey", "benchmark", "vlm"]
last_updated: "2026-11-17"
sources: ["[[raw/papers/10_wang2024_ultrasound_foundation_survey.md]]"]
---

# Foundation Models for Ultrasound Image Analysis: A Survey and Benchmarking Study

- **作者**：Haoran Wang, Jiazhen Pan, Yingying Fang, Qi Dou, Pheng-Ann Heng 等
- **發表場合**：Medical Image Analysis (MedIA) / arXiv:2401.12984 (2024)
- **原始文獻依據**：[[raw/papers/10_wang2024_ultrasound_foundation_survey.md]]

---

## 1. 論文核心貢獻
本文是首篇全面系統化回顧**基礎模型（Foundation Models, FMs）在超音波醫學影像領域的最新進展與多中心標竿評測綜述**。涵蓋視覺基礎模型（VFMs）、視覺語言多模態模型（VLMs）以及自監督預訓練框架，並建立了涵蓋 14 個跨中心臨床資料集（心臟、乳腺、甲狀腺、婦產科、腹部）的開源測試基準。

---

## 2. 超音波 AI 技術的三波演進演繹
1. **第一波（2015-2020）：專門任務的小型 CNN**
   - 代表：標準 [[ronneberger2015_unet|U-Net]]、ResNet。
   - 特徵：依賴單一中心、私有小樣本（常小於 500 例）監督訓練，跨機型/探頭泛化能力低。
2. **第二波（2020-2022）：自監督預訓練與 Vision Transformer**
   - 代表：[[jiao2020_uscl_contrastive|USCL]]、Swin-Unet。
   - 特徵：透過無監督時序預訓練學習解剖特徵，利用自注意力捕捉大範圍病灶與組織關聯。
3. **第三波（2023-現在）：超音波專用大模型與多模態代理**
   - 代表：[[lin2023_samus|SAMUS]]、Ultra-FM、US-LLaVA。
   - 特徵：通用提示分割（Promptable Segmentation）、圖文報告自動生成、掌上型超音波（POCUS）智慧引導。

---

## 3. 當前基礎模型在超音波領域的關鍵挑戰
- **聲學物理先驗缺失 (Physics Blindness)**：通用自然大模型對聲束折射、聲影衰減與組織聲阻抗缺乏物理建模能力。
- **機型與探頭域轉移 (Scanner Domain Shift)**：高階推車式設備（如 Philips EPIQ）到掌上型微型設備（Butterfly iQ）存在 15-25% 的效能衰退。
- **時序視訊閃爍 (Temporal Inconsistency)**：單幀基礎模型應用於即時動態超音波心動圖時出現邊緣閃爍與時間不一致性。

---

## 4. 關聯頁面 (Wiki Links)
- **技術綜述**：[[foundation_models_ultrasound|超音波基礎模型現狀與未來]]
- **歷史演進**：[[ultrasound_ai_evolution|超音波 AI 技術演進史]]
- **代表性適配模型**：[[samus_adapter|SAMUS 模型解析]]
