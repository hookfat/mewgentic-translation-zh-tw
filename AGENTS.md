# AGENTS.md

本檔提供給 AI/代理（agent）執行任務時使用。  
目標：維持 `mewgentic-tw` 翻譯流程一致性，避免破壞原始資料。

## Scope

- 只在目前專案路徑內操作。
- 翻譯任務以 `zh-tw/data/text/` 為唯一修改目標。
- `Output/data/text/` 視為原始來源，只能讀取，不可修改。

## Translation Rules

1. 只修改 `zh-tw/data/text` 下對應 CSV。
2. 翻譯寫入 `en` 欄位。
3. 保留格式標記與占位符，不可破壞：
   - `{catname}`, `{he}`, `{his}`, `{him}`, `{himself}`
   - `[i]...[/i]`, `[b]...[/b]`, `[a:shake]...[/a]` 等標記
4. 長文本需注意斷行可讀性，避免遊戲內顯示擠壓。
5. 避免半翻譯（中英混雜）；除專有名詞外，優先完整翻譯。

## Workflow

1. 以 `Output` 對照 `zh-tw`，找出尚未翻譯條目。
2. 先處理專有名詞，再翻一般文本。
3. 分批翻譯，同批次完成後做英文殘留檢查。
4. 若其他 CSV 出現相同術語，回頭同步既有譯法。

## Glossary Policy

- 術語主檔：`glossary_v1.csv`
- 固定術語匯出：`glossary_fixed_terms_v1.csv`
- 關鍵詞名稱彙整：`glossary_keyword_names_v2.csv`

規則：

1. 新術語優先登錄 `glossary_v1.csv`。
2. 未定案譯名可暫存，允許後續調整。
3. 定案後同步到固定術語檔，並套用到相關 CSV。

## Quality Checklist

- 是否誤改 `Output/data/text/`：必須為否。
- `en` 欄位是否保留原始標記語法：必須為是。
- 是否存在大段英文殘留：應最小化，並註記保留原因（若有）。
- 是否有跨檔案術語不一致：應修正。

