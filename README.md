# 超音波影像研究 LLM Wiki (Ultrasound AI LLM Wiki)

[![GitHub Pages](https://img.shields.io/badge/GitHub%20Pages-Live%20Demo-brightgreen)](https://jimmya0525-abc.github.io/AI_HW10/)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)

專注於「超音波醫學影像人工智慧（Ultrasound AI / PUS AI）」的持久、複利型知識庫，完全借鑑並實踐 **Andrej Karpathy's LLM Wiki** 理念。

---

## 🌟 線上教學簡報 (GitHub Pages)

- **線上公開演示網址 (Live Demo)**：
  👉 **[https://jimmya0525-abc.github.io/AI_HW10/](https://jimmya0525-abc.github.io/AI_HW10/)**
- **直接路徑存取**：
  👉 **[https://jimmya0525-abc.github.io/AI_HW10/wiki/synthesis/ultrasound_intro_slides_v2.html](https://jimmya0525-abc.github.io/AI_HW10/wiki/synthesis/ultrasound_intro_slides_v2.html)**

> **特色功能**：
> - 適合零基礎初學者的 8 頁大字高對比簡報。
> - 內嵌「聲波發射與回聲穿透即時模擬器」，動態展示水純黑（無回聲）與骨純白（強回聲/聲影）。
> - 雙道互動式隨堂小測驗，鞏固「聲阻抗」與「同調斑點干涉」核心觀念。
> - 支援鍵盤左右方向鍵（`←` / `→`）與點狀導航翻頁。

---

## 🏛️ 專案架構 (Three-Layer Architecture)

```
AI_HW10/
├── AGENTS.md                                # 智慧代理維護協議 (中文 Schema 契約)
├── index.html                               # GitHub Pages 首頁入口 (v2 教學簡報)
├── README.md                                # 專案說明文件
├── raw/                                     # 原始文獻庫 (唯讀不可變 Source of Truth)
│   ├── README.md
│   └── papers/                              # 10 篇學術論文原始文字與摘要
└── wiki/                                    # 編譯知識庫 (LLM 寫作與雙向鏈接)
    ├── index.md                             # 全域內容目錄導航
    ├── log.md                               # Append-only 審計日誌
    ├── papers/                              # 10 篇論文深度解析筆記
    ├── concepts/                            # 聲學物理與核心理論概念
    ├── methods/                             # 深度學習模型與波束成形演算法
    ├── tasks/                               # 臨床與工程關鍵任務
    ├── datasets/                            # 全球標竿公開資料集專題
    └── synthesis/                           # 跨文獻綜述與互動簡報
        ├── ultrasound_intro_slides_v2.html  # v2 互動簡報 (最新版)
        ├── ultrasound_intro_slides.html     # v1 互動簡報 (初版存檔)
        ├── ultrasound_ai_evolution.md       # 技術演進全景綜述
        └── acoustic_challenges_matrix.md    # 聲學物理限制對抗矩陣
```

---

## 📚 已攝取之 10 篇代表性學術文獻

1. **U-Net 醫學分割奠基** (MICCAI 2015) — Ronneberger et al.
2. **BUSI 乳腺超音波基準資料集** (Data in Brief 2020) — Al-Dhabyani et al.
3. **CAMUS 心臟超音波分割基準** (IEEE TMI 2019) — Leclerc et al.
4. **SAMUS 超音波專用大模型適配** (IEEE TMI 2023) — Lin et al.
5. **EchoNet-Dynamic 萬例視訊心臟功能分析** (Nature 2020) — Ouyang et al.
6. **HC18 產前胎兒頭圍挑戰賽** (PLOS ONE 2018) — van den Heuvel et al.
7. **ULM 超快顯微定位突破繞射極限** (Nature 2015) — Errico et al.
8. **深度神經網路前端 RF 波束成形** (IEEE TUFFC 2018) — Luchies & Byram
9. **USCL 超音波聲學物理自監督對比學習** (MICCAI 2020 / TMI 2023) — Jiao et al.
10. **超音波基礎模型綜述與標竿評測** (MedIA 2024) — Wang et al.

---

## 🛠️ 如何在 Obsidian 中開啟瀏覽

1. 安裝並開啟 [Obsidian](https://obsidian.md/)。
2. 選擇「開啟現有資料夾作為儲存庫（Open folder as vault）」。
3. 選取本專案目錄 `AI_HW10`。
4. 開啟圖譜視圖（Graph View），即可享受概念、任務、資料集與論文之間交織的拓撲網絡！
