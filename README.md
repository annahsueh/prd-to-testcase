# 📋 PRD → Test Case — Claude Skill

🧾 丟一份 Notion PRD 進來，自動拆成幾十筆測項，寫成 Notion 資料庫。

## 這是什麼？

把 PRD 規格拆解成可執行的測試案例，直接建成 Notion 測試案例資料庫。你只要提供：

- 📄 **Notion PRD 連結** — 要轉成測項的規格文件
- 📁 **Notion 測試回報文件連結** — 資料庫要建在這份文件底下
- 🎨 參考範本 Test Case 連結（選用）— 用來對齊你團隊的寫法

Claude 會完整讀完 PRD（含表格、User Story、埋點表、被劃刪除線的段落），切成 A～J 大類，展開成 60～100 筆測項，然後建一個新子頁面把資料庫放進去。

## 產出長什麼樣

固定 9 欄，由左至右：

| 測試項目 | 類別 | 平台 | 前置條件 | 預期結果 | 測試資料 | 結果 | 備註 | 檔案 |
|---|---|---|---|---|---|---|---|---|
| 標題 | 多選 | 選取 | 文字 | 文字 | 文字 | 狀態 | 文字 | 檔案和媒體 |

編號一律 `A-01`、`A-02`…`J-09`（兩位數零補位），並在 view 上鎖 `SORT BY 測試項目 ASC`，保證由上往下依序不亂。文字欄位開自動換行。

## 它會幫你抓出規格問題

這是這支 skill 最有價值的部分 —— 它**不會**自己幫 PRD 補洞，而是把問題標出來：

- PRD 前後矛盾（例如規格表說「不會有錯誤訊息」但 User Story 寫了錯誤文案）→ 寫成測項，備註註明矛盾出處
- 未定義的行為 → 預期結果寫「依規格確認…」，備註寫「需與 PM 確認」
- 被劃刪除線的功能 → 產生反向測項（「選單內不應出現該選項」）

## 安裝

```bash
/plugin marketplace add annahsueh/claude-skills
/plugin install prd-to-testcase@pressplay-qa
```

或手動放進 skills 資料夾：

```bash
git clone https://github.com/annahsueh/prd-to-testcase.git
cp -r prd-to-testcase/skills/prd-to-testcase ~/.claude/skills/prd-to-testcase
```

## 需要什麼工具？

| 工具 | 用途 | 必要？ |
|---|---|---|
| Notion MCP | 讀 PRD、建立測試案例資料庫 | ✅ |

## 使用方式

```
/prd-to-testcase
```

或直接說：

> 「幫我把這份 PRD 轉成測項」
> 「依照過去習慣，把規格寫到這份測試文件」
> 「這是 PRD、這是測試文件，幫我跑一遍」

缺連結的話 Claude 會主動問，不會自己猜。

## 客製

`SKILL.md` 裡「硬規則」那一段是團隊慣例（欄位命名、子頁面結構、編號規則），要改就改那裡。分類 A～J 的名稱是每份 PRD 各自決定的，不需要改 skill。

---

Made with 🧡 by 薛安妤 — PressPlay
