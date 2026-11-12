# AGENTS.md — 研究知識庫維護規範 (LLM Wiki)

本文件為 AI Agent（如 Codex、Claude Code、OpenCode 等）維護本 **研究知識庫（LLM Wiki）** 的核心架構與操作規範。

> **核心理念**：不同於傳統 RAG 在每次提問時才從零檢索片段，本知識庫採用「持續編譯、增量維護」模式。`wiki/` 是由你（LLM）全權撰寫與維護的結構化 Markdown 知識圖譜，坐落於人類與原始資料之間。每次加入新論文或文章時，你不只做摘要，而是將新知識**編譯並整合**進既有的概念頁、模型頁與總覽中，標記觀點衝突並更新交叉引用，讓知識隨時間複利成長。

---

## 1. 架構與目錄結構

本知識庫分為四個嚴格區分的層級：

1. **原始資料層（`raw/`）— 唯讀的真實來源（Source of Truth）**
   - 存放使用者蒐集的論文 PDF/Markdown、技術部落格文章（如 Obsidian Web Clipper 擷取）、會議/Podcast 逐字稿與圖片資產。
   - **絕對規則**：你只能**讀取** `raw/` 中的檔案，**嚴禁修改或刪除**任何 `raw/` 內容。
2. **維基知識層（`wiki/`）— 由 LLM 維護的知識庫**
   - 存放由你撰寫、更新與互連的 Markdown 頁面。人類負責閱讀、探索與策展；你負責撰寫、交叉引用、衝突標記與日常維護。
3. **研究產出層（`notes/` 與 `presentations/`）— 基於 Wiki 知識邊界的應用產出**
   - 存放嚴格依據 `wiki/` 現有知識產出的專題研究筆記、簡報逐頁腳本與 HTML 簡報。
4. **規範層（`AGENTS.md`）— 本文件**
   - 定義目錄結構、頁面格式與工作流程。隨著研究深入，你應與使用者共同演進本規範。

### 目錄樹

```text
.
├── AGENTS.md                      # 本規範文件（Agent 必讀）
├── README.md                      # 知識庫使用說明與 Obsidian 設定指南
├── raw/                           # 【唯讀】原始資料層
│   ├── papers/                    # 論文原文（PDF 或轉檔後的 Markdown）
│   ├── articles/                  # 技術部落格、報導、Web Clipper 擷取文章
│   ├── notes/                     # 個人靈感、講座/Podcast 筆記、討論逐字稿
│   └── assets/                    # 下載到本地的架構圖、實驗圖表
├── wiki/                          # 【LLM 維護】互連知識庫
│   ├── index.md                   # 內容導向總目錄（依類別列出所有頁面與一句話摘要）
│   ├── log.md                     # 時間導向操作日誌（僅能附加，供追蹤演化歷程）
│   ├── overview.md                # 研究全局綜述與持續演進的核心論點
│   ├── papers/                    # 單篇論文精讀與結構化摘要
│   ├── concepts/                  # 核心技術與概念頁
│   ├── models/                    # 模型、架構與系統頁
│   ├── comparisons/               # 由查詢沉澱而成的專題比較與深度分析
│   └── _templates/                # 各類頁面標準範本
├── notes/                         # 【擴充應用 1】嚴格依 wiki/ 現有知識撰寫的研究筆記 (.md)
└── presentations/                 # 【擴充應用 2 & 3】簡報產出區
    ├── outlines/                  # 簡報逐頁內容腳本 (.md)
    └── html/                      # 可直接於瀏覽器播放的單檔 HTML 簡報 (.html)
```

---

## 2. 頁面格式與 Obsidian 整合規範

本知識庫設計為搭配 **Obsidian** 使用（Obsidian 是 IDE，你是工程師，Wiki 是 Codebase）。所有 `wiki/` 內的頁面（`index.md` 與 `log.md` 除外）皆須遵守以下格式：

### 2.1 YAML Frontmatter（相容 Dataview）

```yaml
---
title: 頁面標題
type: paper | concept | model | comparison | overview
tags:
  - 相關主題標籤
created: YYYY-MM-DD
updated: YYYY-MM-DD
sources:
  - "[[相關原始資料或論文頁面]]"
status: seed | growing | evergreen
---
```

- `status` 定義：`seed`（初建草稿）、`growing`（持續補充中）、`evergreen`（經多篇文獻交叉驗證的成熟頁面）。

### 2.2 連結與引用紀律

- **雙向連結（Wikilinks）**：在內文提及任何重要概念、模型、論文或比較專題時，使用 `[[頁面名稱]]` 或 `[[頁面名稱|顯示文字]]` 建立連結，維持 Obsidian Graph View 的連通性。
- **來源可追溯**：所有數據、Benchmark 分數、實驗參數或核心論點，必須標註來源（如 `（來源：[[1706-microvia-pth-one-bath]]）`）。
- **數學公式**：統一使用標準 LaTeX 語法（行內 `$...$`、獨立區塊 `$$...$$`）。

### 2.3 觀點衝突與過時資訊標記

當新讀入的論文與既有頁面結論矛盾，或推翻舊有假設時，**不可直接靜默覆蓋舊內容**，應保留脈絡並使用 Obsidian Callout 顯式標記：

```markdown
> [!warning] 觀點衝突 / 結論更新
> - **早期觀點**：...（來源：[[舊論文]]）
> - **最新實證**：...（來源：[[新論文]]，YYYY-MM-DD 更新）
```

---

## 3. 核心操作工作流（Operations）

### 操作一：Ingest（吸收與編譯新資料）

每當使用者提供或貼上新文章/論文時，依序執行：
1. **保存原始檔至 `raw/`**：將原始檔案或內容直接存於 `raw/papers/`、`raw/articles/` 或 `raw/notes/`（**唯讀不改**）。
2. **撰寫論文/來源摘要頁**：參照 `wiki/_templates/` 在 `wiki/papers/` 建立對應頁面。
3. **更新關聯的概念與模型頁**：檢查並更新所有相關的 `wiki/concepts/`、`wiki/models/` 與 `wiki/overview.md`（補充數據、機制與衝突標記）。
4. **更新索引與日誌**：同步更新 `wiki/index.md`，並在 `wiki/log.md` 最末端附加 `## [YYYY-MM-DD] ingest | <標題>`。

---

### 操作二：Query（查詢與知識沉澱）

當使用者針對知識庫提問時：
1. 先讀取 `wiki/index.md` 定位相關頁面，再深入讀取對應的 `wiki/` 頁面（必要時回溯 `raw/` 核對）。
2. 產出帶 `[[Wikilinks]]` 與來源引用的回答。
3. 有價值的比較或綜合分析可歸檔至 `wiki/comparisons/`，並更新 `index.md` 與 `log.md`。

---

### 操作三：Lint（定期健康檢查）

全面掃描 `wiki/`，檢查觀點矛盾、孤島頁面（Orphan pages）、高頻提及但缺頁的概念、遺漏的交叉引用與研究缺口，並在 `wiki/log.md` 記錄 `## [YYYY-MM-DD] lint | 知識庫健康檢查`。

---

### 操作四：Research & Presentation Pipeline（研究筆記與簡報產出擴充流程）

當使用者提出一個研究問題或指定專題，要求執行擴充應用產出時，嚴格依序執行以下三步驟：

1. **步驟 1：嚴格知識邊界的研究筆記（存於 `notes/`）**
   - **知識邊界原則（極重要）**：筆記正文**必須 100% 完全依據 `wiki/` 內現有的知識與數據撰寫**，明確標註來自哪個 `[[wiki頁面]]`。
   - **網路搜尋與隔離規則**：同時上網搜尋該主題的相關最新文獻與資料，**但尚未存入 `wiki/` 的外部內容嚴禁混入筆記正文（也不得用於後續簡報）**。
   - **建議參考文獻清單（可點擊下載）**：將網路搜尋找到、但尚未收錄於 `wiki/` 的外部文獻（含標題、作者/機構、年份、推薦理由），統一列在該筆記最末端的 `## 建議參考文獻（待整理至 Wiki，點擊即可下載）` 區塊，並**優先附上可直接點擊下載 PDF 或開放取用原文的超連結**，供使用者一鍵下載後納入 `raw/`。
   - **LaTeX 數學支援**：筆記正文之數學公式統一使用標準 LaTeX 語法（`$...$` 與 `$$...$$`）。
   - 檔名格式：`notes/YYYY-MM-DD-<主題代號>.md`。

2. **步驟 2：簡報逐頁內容腳本（存於 `presentations/outlines/`）**
   - 完全依據步驟 1 的 `notes/` 正文（不含尚未納入 Wiki 的外部參考文獻內容），規劃並撰寫逐頁投影片內容，包含：頁碼與投影片標題、核心論點（Assertion-Evidence）、建議視覺/圖表呈現方式、以及講者備忘（Speaker Notes）。
   - 檔名格式：`presentations/outlines/YYYY-MM-DD-<主題代號>-outline.md`。

3. **步驟 3：HTML 互動簡報（存於 `presentations/html/`）**
   - 依據步驟 2 的逐頁內容，製作單檔、可於瀏覽器開啟的現代化 HTML 簡報（支援鍵盤左右鍵/按鈕翻頁、頁碼進度條、講者備忘切換、清晰排版與表格呈現，並內建 **KaTeX / MathJax LaTeX 數學公式渲染**）。
   - 檔名格式：`presentations/html/YYYY-MM-DD-<主題代號>.html`。

---

## 4. 索引與日誌規範

- **`wiki/index.md`**：按類別列出所有頁面與一句話摘要。
- **`wiki/log.md`**：純附加（Append-only），每筆紀錄以 `## [YYYY-MM-DD] <ingest|query|lint|init|research> | <簡短標題>` 開頭。