# 知識庫演化日誌 (Log)

本檔案為**純附加（Append-only）**的時間軸紀錄，記錄每次 `ingest`、`query` 歸檔與 `lint` 健康檢查。
可使用 `grep "^## \[" wiki/log.md | tail -10` 快速查看近期操作。

---

## [2026-11-12] init | 初始化 LLM 研究知識庫
- 建立 `AGENTS.md` 中文規範文件
- 建立 `raw/`（`papers/`、`articles/`、`notes/`、`assets/`）與 `wiki/`（`papers/`、`concepts/`、`models/`、`comparisons/`、`_templates/`）目錄結構
- 初始化 `wiki/index.md`、`wiki/log.md` 與 `wiki/overview.md`

## [2026-11-12] ingest | 盲孔填充與通孔電鍍之同鍍槽電鍍技術之研究（許家福, 2017）
- 儲存原始檔案：`raw/papers/2017-許家福-盲孔填充與通孔電鍍之同鍍槽電鍍技術之研究.pdf`
- 新增論文頁：[[1706-microvia-pth-one-bath]]
- 新增概念頁：[[copper-electroplating-additives]]、[[microvia-filling-and-pth]]、[[taguchi-method-in-electroplating]]
- 更新頁面：[[overview]]、[[index]]

## [2026-11-12] init | 擴充研究筆記與簡報產出資料夾結構
- 更新 `AGENTS.md`，新增「操作四：Research & Presentation Pipeline」三步驟規範
- 建立 `notes/`、`presentations/outlines/` 與 `presentations/html/` 資料夾
- 同步 `wiki/papers/1706-microvia-pth-one-bath.md`

## [2026-11-12] research | 同鍍槽盲孔填充與通孔電鍍專題筆記與簡報產出
- 產出研究筆記（嚴格依 Wiki 內容 + LaTeX + 文末可下載參考文獻）：`notes/2026-11-12-microvia-pth-one-bath-research.md`
- 產出簡報逐頁腳本：`presentations/outlines/2026-11-12-microvia-pth-one-bath-outline.md`
- 產出 HTML 簡報（含 KaTeX LaTeX 渲染）：`presentations/html/2026-11-12-microvia-pth-one-bath.html`
