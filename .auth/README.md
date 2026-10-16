# 測試帳號存放說明

> 本目錄用來存放與測試環境相關的憑證、session、cookie 檔案。
> **此目錄下的任何檔案都不應被簽入版本控制。**（Git 若啟用，請加入 `.gitignore`）

## 檔案命名建議
- `accounts.local.md`：以明文表格列出各角色可用的測試帳號（僅存放於本機）
- `target.local.md`：本次測試標的的網址、角色定義、版本字串取得方式、已知外部網域等
- `storage-state-<role>.json`：Playwright 保存的登入狀態
- `cookies-<role>.txt`：手動匯出的 cookie（如需要）

> 範本：`accounts.local.md.example`、`target.local.md.example` 是通用範本，會被 commit；
> 實際填值的 `*.local.md` 由 `.gitignore` 排除，只存在本機。
> 首次 setup：`cp <xxx>.local.md.example <xxx>.local.md` 後編輯填值。

## accounts.local.md 範本
```markdown
| 角色 | 帳號 | 密碼 | 備註 |
|---|---|---|---|
| guest | — | — | 不需登入；用於觀察公開頁 |
| member | <待填> | <待填> | 一般會員，可用於購物流程 |
| admin | <待填> | <待填> | 僅在明確授權後使用 |
```

## 使用規則
1. **不要把密碼寫進 `docs/`、`records/` 或任何會分享給他人的檔案。**
2. 探索報告需要標示角色時，只寫角色名稱（例：`member`），不寫帳號。
3. 若 Playwright MCP 需要讀取 storage state，將路徑放在 `.mcp.json` 或 skill 執行時臨時指定，不要寫死在 `docs/`。
4. 帳號若被鎖定、密碼被重設，請在這裡更新；同時提醒 QA 其他使用者。

## 待辦
- [ ] 由 QA 填入實際測試帳號到 `accounts.local.md`
- [ ] 由 QA 確認每個角色的權限範圍，寫進 `CLAUDE.md` 的「角色」段落