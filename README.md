# QA Agent

以 Claude Code + Playwright MCP 搭建的 QA 探索代理，針對特定網站做：
- **產品地圖建立**（透過 `/map-product` skill）
- **人工補充地圖**（透過 `/annotate-map` skill）
- **探索性測試**（透過 `/explore` skill）

本 repo 是 **PoC 階段**，流程與 skill 定義仍在調整中。設計背景與議題紀錄在 `notes/` 下。

---

## 初次 Setup

```bash
# 1. 複製本機設定範本
cp .mcp.json.example .mcp.json
cp .auth/target.local.md.example .auth/target.local.md
cp .auth/accounts.local.md.example .auth/accounts.local.md

# 2. 編輯填入實際值
#   - .mcp.json：把 --allowed-origins 的 <target-domain> 換成目標網域
#     多個子網域用分號分隔：https://a.com;https://m.a.com
#   - .auth/target.local.md：目標站台的網址、角色、版本字串取得方式、已知外部網域
#   - .auth/accounts.local.md：各角色測試帳號密碼

# 3. 開啟 Claude Code 進入本 repo 目錄
#   按 CLAUDE.md 的規則工作
#   /map-product 建立產品地圖（寫入 docs/）
#   /annotate-map 人工補充或修改地圖（不經探索；寫入 docs/features/）
#   /explore 跑探索性測試（寫入 records/）
#     若要跑結構化需求/spec/test case，把輸入檔放進 inputs/（格式見 inputs/README.md）
```

---

## 檔案結構

| 路徑 | 用途 | 入版本控制 |
|---|---|---|
| `CLAUDE.md` | 專案守則 | ✓ |
| `.claude/skills/explore/` | 探索性測試 skill | ✓ |
| `.claude/skills/map-product/` | 產品地圖 skill | ✓ |
| `.claude/skills/annotate-map/` | 人工補充地圖 skill | ✓ |
| `.mcp.json.example` | Playwright MCP 設定範本 | ✓ |
| `.mcp.json` | 本機實際設定 | ✗ |
| `.auth/README.md` | 憑證存放規範 | ✓ |
| `.auth/*.example` | 範本檔 | ✓ |
| `.auth/*.local.md` | 本機實際憑證/標的資訊 | ✗ |
| `inputs/` | 需求 / spec / test case 放置區（給 `/explore` skill 吃） | ✓ |
| `docs/` | 產品地圖（map-product 產出） | PoC 階段暫 ✗ |
| `records/` | 探索報告（explore 產出） | PoC 階段暫 ✗ |
| `notes/` | 流程設計討論筆記 | ✓ |
| `design/` | QA agent 本身的設計文件（給人閱讀；AI 不讀，見 CLAUDE.md 共通規則 #9） | ✓ |

---

## 使用規則重點

- 所有 AI 自動寫入的內容標為「待確認」，由 QA 審核後改為「已確認」
- `docs/` 只能透過 `/map-product` 或 `/annotate-map` 修改
- 禁止事項與需詢問協定見 `CLAUDE.md`

---

## 相依

- Node.js（跑 Playwright MCP）
- Python（如需跑其他輔助腳本；`pip install -r requirements.txt`）
- Claude Code
