# LLM 研究個人知識庫（LLM Wiki）

本專案採用 Andrej Karpathy 提出的 **LLM Wiki** 架構，結合 **Obsidian** 與 **AI Coding Agent**（如 Claude Code、Codex、OpenCode），打造一個隨閱讀與研究持續複利成長的 LLM 研究知識庫。

## 快速開始

1. **用 Obsidian 開啟本資料夾**：選擇 `Open folder as vault`，即可透過 Graph View 檢視概念與論文的連結網路。
2. **用 AI Agent 開啟本資料夾**：Agent 會自動讀取根目錄的 `AGENTS.md` 作為操作規範。
3. **開始累積知識**：
   - 將論文 PDF/Markdown 放入 `raw/papers/`，或用 Obsidian Web Clipper 將技術文章存至 `raw/articles/`。
   - 對 Agent 下達指令：`請依照 AGENTS.md 吸收並整理 raw/papers/xxx.pdf`。
   - 提問時要求整理比較：`請比較 ... 並將結果歸檔到 wiki/comparisons/`。
   - 定期執行健檢：`請對 wiki/ 執行一次 lint 健康檢查`。

## 目錄說明

- `AGENTS.md`：給 AI Agent 閱讀的知識庫維護憲章。
- `raw/`：原始資料區（論文、文章、筆記、圖片），**唯讀不改**。
- `wiki/`：由 AI Agent 撰寫與維護的 Markdown 知識庫。
  - `wiki/index.md`：內容總目錄。
  - `wiki/log.md`：時間軸操作日誌。
  - `wiki/overview.md`：LLM 研究全局綜述。
  - `wiki/_templates/`：各類筆記標準範本。

## 擴充應用目錄

- `notes/`：嚴格僅依據 `wiki/` 現有內容撰寫的研究筆記（文末附網路搜尋之「建議參考文獻」供後續決定是否納入 Wiki）。
- `presentations/outlines/`：根據 `notes/` 製作的簡報逐頁內容腳本（`.md`）。
- `presentations/html/`：根據逐頁腳本製作的互動式單檔 HTML 簡報（`.html`）。
