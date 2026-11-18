# AGENTS.md — 超音波影像研究 LLM Wiki 維護規範

本文件是本知識庫（LLM Wiki）的核心架構協議（Schema & Rules）。凡在此專案工作的 LLM 智慧代理（Agent），必須嚴格遵守本文件所定義的架構、目錄規範、寫作慣例與操作流程（SOP）。

---

## 1. 核心理念與定位 (Core Philosophy)

本專案借鑑 **Andrej Karpathy's LLM Wiki** 模式，打造一個**專注於「超音波醫學影像人工智慧（Ultrasound AI / PUS AI）」的持久、複利型知識庫**。

- **超越傳統 RAG**：傳統檢索增強生成（RAG）在每次查詢時從原始片段重新推導答案，缺乏累積效應。LLM Wiki 則是**即時編譯並維護結構化知識庫**，所有跨文件交叉引用、矛盾對比、演進脈絡皆已預先整理，知識庫隨時間與文獻累積而不斷成長。
- **角色分工**：
  - **人類研究者（User）**：負責挑選來源文獻、設定研究主題、引導研究方向、提出關鍵問題。
  - **AI 代理（LLM Agent）**：全權負責知識庫的寫作、交叉引用、索引維護、矛盾標記與簿記整理。
  - **Obsidian 作為 IDE**：使用者透過雙向鏈接與圖譜視圖（Graph View）探索知識庫，LLM 則是這座代碼庫（Codebase）的專職工程師。

---

## 2. 三層架構 (Three-Layer Architecture)

```
[原始文獻層 raw/] (唯讀不可變) ──> [LLM 編譯與整合] ──> [維護管理層 wiki/]
                                                               │
                                  [架構契約 AGENTS.md] <───────┘
```

1. **原始來源層 (`raw/`)**：
   - 存放論文原件、預印本摘要、PDF 轉出的 Markdown 文件或臨床筆記。
   - **完全唯讀且不可變（Immutable）**，LLM 僅能讀取，絕不可修改或刪除。這是唯一的真實之源（Source of Truth）。
2. **Wiki 知識層 (`wiki/`)**：
   - 完全由 LLM 生成與維護的 Markdown 文件，包含實體頁、概念頁、方法頁、臨床任務頁、資料集頁、論文解析頁與綜合分析報告。
   - 具備強雙向鏈接（`[[頁面名稱]]`）與標準 YAML Frontmatter。
3. **規範協議層 (`AGENTS.md`)**：
   - 即本文件，規定所有操作規則、目錄層次、更新規範與防護邊界。

---

## 3. 目錄結構與分類體系 (Directory Structure)

專案根目錄嚴格依循下列劃分：

```text
├── AGENTS.md                     # 本規範文件
├── raw/                          # 原始文獻庫 (唯讀)
│   └── papers/                   # 論文原始文字、摘要與元數據
└── wiki/                         # 編譯後的持久知識庫 (LLM 維護)
    ├── index.md                  # 內容全域索引目錄 (分類條列 + 單行摘要)
    ├── log.md                    # 時間軸操作紀錄 (Append-only 審計日誌)
    ├── papers/                   # 單篇論文的深度精讀筆記與解析
    ├── concepts/                 # 超音波物理、聲學現象與核心理論
    ├── methods/                  # 深度學習模型、演算法與架構
    ├── tasks/                    # 臨床與工程任務 (分割、分類、超解析度等)
    ├── datasets/                 # 公開與臨床標竿資料集 (BUSI, CAMUS 等)
    └── synthesis/                # 專題綜述、技術演進圖譜、交叉對比報告
```

---

## 4. 命名與鏈接慣例 (Conventions)

1. **文件名與雙向鏈接**：
   - 使用英語小寫或標準英文術語作為檔名，單詞間以底線 `_` 連接，例如：`speckle_noise.md`、`busi_dataset.md`。
   - 在 Markdown 正文中一律使用 Obsidian 風格雙向鏈接：`[[speckle_noise|斑點噪聲 (Speckle Noise)]]` 或 `[[busi_dataset|BUSI 資料集]]`。
   - 必須確保鏈接目標檔案確實存在，禁止產生無效死鏈。
2. **YAML Frontmatter**：
   每篇 wiki 頁面開頭必須包含標準元數據：
   ```yaml
   ---
   title: "頁面標題 (中英文對照)"
   aliases: ["別名1", "Alias 2"]
   category: "concept | method | task | dataset | paper | synthesis"
   tags: ["ultrasound", "deep-learning", "segmentation"]
   last_updated: "YYYY-MM-DD"
   sources: ["[[source_paper_1]]", "[[source_paper_2]]"]
   ---
   ```
3. **語言原則**：
   - 內文主要以**繁體中文**撰寫，學術術語首次出現時需附帶標準英文（如：動態範圍壓縮 Dynamic Range Compression、光束成形 Beamforming）。

---

## 5. 核心操作流程 (Core Workflows)

### 流程一：文獻攝取 (Ingest Workflow)
當在 `raw/papers/` 新增論文或收到攝取指令時，LLM 必須按以下步驟執行：
1. **閱讀與解析 (Read)**：完整閱讀原始文獻，提煉核心貢獻、數學/模型架構、臨床應用場景、實驗結果與侷限性。
2. **建立論文筆記 (Create Paper Note)**：在 `wiki/papers/` 建立詳細筆記，引用原始資料來源。
3. **網絡更新 (Graph Update)**：
   - 檢查並更新 `wiki/concepts/`：若論文提出新物理機制或聲學理論，創建或補充該概念頁。
   - 檢查並更新 `wiki/methods/`：更新相關模型架構頁（如 U-Net, SAMUS, Contrastive Learning），納入本篇的改進點與實驗數據。
   - 檢查並更新 `wiki/tasks/`：在臨床任務頁面（如乳腺腫瘤分割、心臟射血分數評估）追加 SOTA 表現或最新技術進展。
   - 檢查並更新 `wiki/datasets/`：紀錄該資料集的評估基準、數據切分與評測結果。
4. **衝突與演進偵測 (Contradiction & Evolution)**：若本篇成果推翻或顯著修正了舊論文的論點（例如傳統濾波 vs 深度學習抗斑點噪聲），需在舊頁面上標註最新文獻的修正。
5. **更新索引 (`wiki/index.md`)**：將新建立或修改的頁面更新至索引中，並附上一句話摘要。
6. **追加紀錄 (`wiki/log.md`)**：依照時間軸寫入一行操作記錄：
   `## [YYYY-MM-DD] ingest | 論文名稱或文獻代號`，簡述變更了哪些檔案。

---

### 流程二：問答與複利回填 (Query & Compound Workflow)
當使用者針對超音波領域提出研究問題或尋求技術對比時：
1. **檢索導航**：首先檢查 `wiki/index.md` 與相關 concept/method/task 頁面。
2. **深度合成**：綜合多篇論文的觀點與數據進行回答，並提供精確的引用來源（雙向鏈接）。
3. **知識沉澱 (Compound)**：若產生的回答具有高度價值（例如跨架構性能比較表、臨床挑戰分析、技術演進趨勢），**不得僅留在對話中**，應將其編寫為 `wiki/synthesis/` 的新頁面，並同步更新至 `wiki/index.md` 與 `wiki/log.md`。

---

### 流程三：健康檢查 (Lint Workflow)
定期檢查維護知識庫品質：
1. **孤島檢查 (Orphan Pages)**：找出沒有被任何頁面引用的獨立頁面，建立關聯。
2. **斷鏈修復 (Broken Links)**：修正拼寫錯誤或指向不存在文件的雙向鏈接。
3. **概念盲點 (Missing Concepts)**：檢視在多篇論文中被重複提及但尚未獨立成頁的重要專有名詞，主動補全頁面。
4. **過時標記 (Stale Claims)**：標記已經被更新研究超越的方法或結論。

---

## 6. 特殊檔案格式定義

### `wiki/index.md` 規範
按領域劃分（概念、方法、臨床任務、資料集、論文精讀、綜合分析），每項採用：
`- [[檔案名|顯示名稱]] — 一句話核心總結（包含關鍵標籤或年份）`。

### `wiki/log.md` 規範
採用嚴格格式以利檢索：
```markdown
# Wiki Operation Log

## [YYYY-MM-DD] ingest | 論文標題
- **新增檔案**: `wiki/papers/...`
- **更新實體**: `wiki/concepts/...`, `wiki/methods/...`
- **操作摘要**: 提取了 xxx 方法，更新了 yyy 基準表現。
```
