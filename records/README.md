# records/

> 每次探索的報告放在這裡。截圖、HAR、trace 等 artifact 放在 `artifacts/`。

## 命名規則
- 報告檔：`YYYY-MM-DD-<topic>.md`（topic 用 kebab-case，例：`2026-10-08-coupon-code.md`）
- 若同一天同一主題有多次，加序號：`YYYY-MM-DD-<topic>-02.md`

## artifacts/ 子目錄
- Playwright MCP 的 `--output-dir` 指向 `records/artifacts`，截圖、trace 會寫在這裡
- 建議再按日期分子資料夾：`artifacts/YYYY-MM-DD-<topic>/screenshot-01.png`
- 體積過大時（例：單次探索 > 50MB）請整理或移至外部儲存，並在報告留連結

## 報告格式
以 `.claude/skills/explore/SKILL.md` 的「格式 → 報告」段落為準，不要在此另立一份。重點提醒：
- 「建議的地圖修正」用表格（檔案 / 項目 / 目前內容 / 實機觀察），不用 bullet
- 原則見 CLAUDE.md 共通規則，不在此重複