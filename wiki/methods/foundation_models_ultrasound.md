---
title: "超音波領域基礎模型 (Foundation Models in Ultrasound) 發展現狀"
aliases: ["Ultrasound Foundation Models", "US-FM", "超音波大模型", "VLM in Ultrasound"]
category: "method"
tags: ["foundation-model", "vlm", "peft", "adapter", "sam", "clip"]
last_updated: "2026-11-17"
sources: ["[[wang2024_ultrasound_foundation_survey]]", "[[lin2023_samus]]"]
---

# 超音波領域基礎模型 (Foundation Models in Ultrasound)

## 1. 概念演進：從特定單一任務邁向通用智慧
傳統超音波 AI（如單一任務的 [[unet_architecture|U-Net]]）往往在特定醫療院所、特定超音波機型（如 GE、Philips）訓練，一旦換到其他型號探頭或掌上型微型設備（POCUS），性能即大幅崩跌。
近年來，以大語言模型（LLM）與視覺基礎模型（如 SAM、CLIP、DINOv2）為代表的**基礎模型（Foundation Models, FMs）**典範席捲醫學影像，激發了構建**通用超音波基礎模型（Ultrasound Foundation Models, US-FMs）**的研究熱潮。

---

## 2. 三大核心架構範式
根據 [[wang2024_ultrasound_foundation_survey|Wang et al. (2024)]] 的分類體系，當前超音波大模型主要聚焦三大主流路徑：

```
                              超音波基礎模型 (US-FMs)
                                        │
        ┌───────────────────────────────┼───────────────────────────────┐
        ▼                               ▼                               ▼
[視覺基礎模型微調 (VFMs)]     [視覺-語言多模態模型 (VLMs)]    [自監督聲學預訓練 (SSL)]
- 代表：[[samus_adapter|SAMUS]]- 代表：US-LLaVA, BiomedCLIP     - 代表：[[ultrasound_contrastive_learning|USCL]]
- 核心：Promptable 分割        - 核心：自動超音波報告生成       - 核心：無標註視訊預訓練
- 方法：PEFT / LoRA / Adapter  - 方法：交叉模態對齊 (Align)    - 方法：時序與聲學先驗
```

1. **可提示的通用視覺分割模型 (Promptable VFMs)**：
   - 以 [[samus_adapter|SAMUS]] 為典型代表。透過適配層將通用基礎模型（SAM）的拓撲分割能力遷移至各人體器官（乳腺、甲狀腺、心臟、胎兒），允許醫生以點選（Point）或框選（BBox）方式進行極速交互式診斷。
2. **超音波視覺-語言多模態模型 (Vision-Language Models, VLMs)**：
   - 結合大型語言模型（LLM）與超音波特徵提取器，直接讀取連續超音波影像並自動產出標準化臨床超音波檢查報告（如 BI-RADS 診斷描述、肌腱撕裂程度判定）。
3. **聲學物理引導的自監督預訓練 (Physics-informed SSL)**：
   - 如 [[ultrasound_contrastive_learning|USCL]]，利用數十萬例無標註超音波視訊提取底層聲學表徵。

---

## 3. 當前開放挑戰與未來方向
1. **跨機型與跨探頭域適應 (Vendor & Probe Generalization)**：
   高階彩色推車機與便攜式探頭間的中心頻率、動態範圍和波束成形演算法不同，基礎模型需具備自適應域對齊能力。
2. **時序視訊一致性 (Temporal Cine Coherence)**：
   現有 2D 基礎模型直接逐幀處理心動圖或胎兒視訊時，會出現邊界跳動與閃爍問題，亟需融合時空注意力機制（如 [[echonet_spatiotemporal|EchoNet]]）。
3. **聲學物理先驗深度融合**：
   現有 Transformer 模型本質上仍將超音波視為一般光學像素陣列，未來需將聲速分佈、探頭孔徑幾何、[[beamforming_physics|波束成形前端物理]] 直接內嵌至模型注意力機制中。

---

## 4. 關聯頁面 (Wiki Links)
- **領域綜述論文**：[[wang2024_ultrasound_foundation_survey|Wang et al. 2024 綜述評測]]
- **專用微調模型**：[[samus_adapter|SAMUS 適配架構]]
- **演進史對比**：[[ultrasound_ai_evolution|超音波 AI 技術演進史]]
