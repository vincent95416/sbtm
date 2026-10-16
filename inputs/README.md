# inputs/

> 需求、spec、test case 的放置區。可選用；也可以直接貼在對話中給 Claude Code。

## 命名建議
- `YYYY-MM-DD-<topic>.md`：單一需求或 spec
- `YYYY-MM-DD-<topic>/`：若包含截圖、附件，建一個資料夾

## 檔案內容建議（給 Claude Code 容易拆解）
```markdown
# <需求 / spec 標題>
- 來源：<JIRA / Notion / Email / 口述>
- 相關模組：<例：結帳 / 會員 / 搜尋>
- 版本或 build：<可選>

## 要驗證的點
1. ...
2. ...

## 已知前置條件
- 需要的角色、資料、功能開關

## 不要測試
- 列出不希望 AI 碰觸的範圍（例：真實付款、刪除資料）
```

## 使用方式
- 將輸入檔放進此目錄後，告訴 Claude Code：「請依 `inputs/<檔名>` 執行 explore skill」
- Claude Code 會依 `.claude/skills/explore/SKILL.md` 的流程產出 charter 給 QA 確認，再開始探索