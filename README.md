# mewgentic-tw

`mewgentic` 繁體中文在地化專案。

本專案的目標是將遊戲文字 CSV 的 `en` 欄位改為繁體中文，供遊戲內選擇英文語系時顯示中文內容。

## 目錄結構

- `Output/data/text/`
  - 原始解包文本（唯讀參考來源，不直接修改）
- `zh-tw/data/text/`
  - 實際翻譯檔案（直接修改這裡的 `en` 欄位）
- `glossary_v1.csv`
  - 術語表主檔
- `glossary_fixed_terms_v1.csv`
  - 已確認固定用語匯出
- `glossary_keyword_names_v2.csv`
  - 關鍵詞名稱彙整

## 翻譯規則

1. 不修改 `Output/data/text` 原始檔。
2. 只修改 `zh-tw/data/text` 下對應 CSV。
3. 翻譯寫入 `en` 欄位。
4. 保留格式標記與變數占位符，例如：
   - `{catname}`, `{he}`, `{his}`, `{him}`
   - `[i]...[/i]`, `[b]...[/b]`, `[a:shake]...[/a]`
5. 長文本需注意換行可讀性與遊戲內顯示。

## 建議流程

1. 以 `Output` 對照 `zh-tw`，找出尚未翻譯條目。
2. 先翻專有名詞並同步術語表。
3. 逐批翻譯一般文本，避免半翻譯（中英混雜）。
4. 完成單一 CSV 後做一次殘留英文檢查。
5. 若不同 CSV 出現相同術語，回頭同步既有譯法。

## 術語表維護

- 新增術語時，優先寫入 `glossary_v1.csv`。
- 若譯名尚未定案，可先標記為可調整版本。
- 固定後再匯出到 `glossary_fixed_terms_v1.csv` 供後續自動替換或人工對照。

## 目前狀態

- `zh-tw/data/text/events.csv`：已完成翻譯。
- 其餘 CSV：持續翻譯與同步術語中。

