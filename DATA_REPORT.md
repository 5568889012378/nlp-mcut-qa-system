# 資料前處理報告 (Data Preparation Report)

> 期中評量 · NLP 自然語言處理 115-S1
> 填寫方式：請把所有「（ ）」與 `___` 替換成你自己的內容，並刪除 `>` 開頭的說明文字。

- **學號 / 姓名**：U12627023/陳宏哲
- **專案名稱**：___
- **完成的任務**：- [ ] 1-A 頁首頁尾清除　- [ ] 1-B 雙語標題合併　- [ ] 1-C 雙語條文合併

---

## 1. 資料集概覽 (Dataset Overview)

> 數字來源：`01_Data_Ingestion.ipynb` 第 2 節 (掃描 PDF) 與第 5 節 (批次處理) 的輸出。

| 類別 (Cluster) | PDF 數量 | 清洗前 chunk 數 | 清洗後 chunk 數 |
|---|---|---|---|
| （例：Academic_Affairs） | | | |
| | | | |
| **合計** | | | |

**問題 (2–3 句)：** 清洗後 chunk 數量變少了多少？是哪個任務造成的？有沒有哪個任務**不影響** chunk 數量？為什麼？

> 提示：chunk 是用什麼規則切開的？請看 notebook 第 5 節的 `chunking_regex`。

___

## 2. 清洗步驟 (Cleaning Steps)

> **截圖來源：** `data/interim/<類別>/` 中的 `raw_*.md` (清洗前) 與 `cleaned_*.md` (清洗後)，也就是批次處理存下的**真實檔案**。
>
> **[重要] 不可使用 notebook 中的範例。** notebook 任務 1-A、1-B、1-C 的測試文字 (第二十一條、明志科技大學 / Ming Chi University of Technology、第十五條 / Article 15) **不能**作為你的截圖。請在真實檔案中**另找一處**，可以是其他 PDF 的檔案。使用範例的截圖**不給分**。
>
> **截圖方法 (VS Code 比較檢視)：**
> 1. 在檔案總管對 `raw_<檔名>.md` 按右鍵 → **Select for Compare**。
> 2. 對同一份文件的 `cleaned_<檔名>.md` 按右鍵 → **Compare with Selected**。
> 3. 左右並排顯示，紅色 = 刪除，綠色 = 新增或修改。按 `Ctrl + F` 搜尋，找到該任務造成的變更。
> 4. 每個任務截**一張**圖，存到 `reports/figures/`，**檔名必須完全相同** (否則圖片不會顯示)：
>    * 任務 1-A → `1a_compare.png`
>    * 任務 1-B → `1b_compare.png`
>    * 任務 1-C → `1c_compare.png`

### 2.1 任務 1-A：頁首頁尾溢出清除

- 檔名：___　搜尋的文字：___
- 截圖 (存為 `reports/figures/1a_compare.png`)：![1-A](reports/figures/1a_compare.png)
- 改變了什麼：___
- 這對之後的問答檢索有什麼幫助：___
- 這個任務有沒有**改錯**的地方 (把不該改的也改了)？若有，寫出檔名與搜尋的文字；若沒有，寫「沒有發現」：___

### 2.2 任務 1-B：雙語標題合併

- 檔名：___　搜尋的文字：___
- 截圖 (存為 `reports/figures/1b_compare.png`)：![1-B](reports/figures/1b_compare.png)
- 改變了什麼：___
- 這對之後的問答檢索有什麼幫助：___
- 這個任務有沒有**改錯**的地方 (把不該改的也改了)？若有，寫出檔名與搜尋的文字；若沒有，寫「沒有發現」：___

### 2.3 任務 1-C：雙語條文合併

- 檔名：___　搜尋的文字：___
- 截圖 (存為 `reports/figures/1c_compare.png`)：![1-C](reports/figures/1c_compare.png)
- 改變了什麼：___
- 這對之後的問答檢索有什麼幫助：___
- 這個任務有沒有**改錯**的地方 (把不該改的也改了)？若有，寫出檔名與搜尋的文字；若沒有，寫「沒有發現」：___

## 3. 評估指標與 AI 解讀查證 (Metrics & Verifying the AI's Interpretation)

### 3.1 指標數據表

> 數字來源：專案根目錄的 `metrics.json`。[1]、[2] 必填；[3]、[4] 選填。
> 「參考值」由老師在課堂上公布 (完成全部任務的結果)。

| 指標 | Raw | Cleaned (你的) | Cleaned (參考值) |
|---|---|---|---|
| [1] 中位數長度 Median Length | 205.0 | 297.0 | 270.5 |
| [2] 拓撲錨定率 TAR | 1.0 | 1.0 | 1.0 |
| [3] 深度變異量 SDV (選填) | 0.0 | 0.0 | 0.0 |
| [4] 中位數資訊熵 Entropy (選填) | 4.720 | 5.138 | 5.062 |

> **儀表板截圖：** 你自己的 `01_Data_Ingestion.ipynb` **第 6 節**輸出的 4 拼圖儀表板 (第 8 週執行並保留的輸出)。截圖後存為 `reports/figures/dashboard.png`。第 3.2 節也會用到這張截圖。

![dashboard](reports/figures/dashboard.png)

你的 Cleaned 結果與參考值一致嗎？若一致，寫「一致」；若不一致，找出原因。（1 句）
不一致是因為 JSON 數據僅提供單點的中位數統計，而圖片則是呈現資料整體分布的箱型圖，兩者比較的基準與型態並不相同
___

### 3.2 AI 的解讀

> 把第 3.1 節的儀表板截圖 (`dashboard.png`) 交給 AI，請它解讀結果。將 AI 的回答**完整貼在這裡**，並註明使用的 AI 工具。

- 使用的 AI 工具：Gemini

```text
夏農資訊熵 (Shannon Information Entropy) 結果解讀根據圖表與數據，針對 Cleaned（清理後） 與 Raw（原始資料） 的夏農資訊熵分佈進行比較：中位數提升：Cleaned 的中位數（箱內橘線）為 5.138，高於 Raw 的 4.720，顯示資料清理後的中位資訊量有所增加。 整體分佈上移：Cleaned 的整體箱體（代表第 25 至第 75 百分位數的四分位距）位置相較於 Raw 明顯偏高。   離群值（Outliers）狀況：兩組資料在低值區間（小於 3）均出現了相似的離群點分佈。   
總結：由於該指標的判定標準為「越高越好（High is good）」，經 Cleaned 處理後的資料在夏農資訊熵表現上優於 Raw，代表資料清理步驟成功提升了整體的資訊豐富度與隨機變異性。 
```

### 3.3 你的查證 (至少兩點)

> 挑 AI 說得最肯定的兩句話，回到你的檔案或程式中找證據：它說的是真的嗎？

**查證 1**
- AI 的說法：Cleaned 的夏農資訊熵 中位數數值為 5.138，高於 Raw 的 4.720
- 我查了什麼 (哪個檔案、哪個 chunk、哪段程式)：metrics.json
- 結論：正確 ，因為 JSON 數據明確記錄 Cleaned ：5.13814769620483、Raw ：4.719958679606001

**查證 2**
- AI 的說法：Cleaned 的中位數（箱內橘線）高於 Raw，且整體箱體位置偏高
- 我查了什麼：上傳的圖片中夏農資訊熵的箱型圖
- 結論：正確 ，因為 表中 Cleaned 的橘色中位數橫線與整個四分位距箱體位置確實高於 Raw

### 3.4 實際證據：你被指定的 chunk

> 執行 `09_midterm_chunks.ipynb`：填入你的學號與老師在課堂上公布的 SEED，按 Run All。
> 每位同學拿到的 chunk 不同。請**連同驗證碼**一起填入。
> 程式只顯示前 400 字元的預覽。請在 VS Code 打開程式列出的**閱讀用檔案** (`data/interim/` 中的 `cleaned_*.md`，與 JSON 內容相同但有正常換行)，按 `Ctrl + G` 輸入程式給的**行號** (或按 `Ctrl + F` 搜尋「搜尋用」文字)，從該行讀到下一個 `## ` 標題為止，就是**完整**的 chunk。

- **SEED**：1106

**(a) 很長的 chunk**
資料檔 (JSON): data/processed/Academic_Affairs/cleaned_A232060013_學生抵免學分辦法_processed.json
閱讀用檔案 (有正常換行): data/interim/Academic_Affairs/cleaned_A232060013_學生抵免學分辦法.md
從第 352 行開始 (VS Code 中按 Ctrl + G，輸入 352，即可跳到這一行)
位置: 第 31 個 chunk (從 0 開始數)，也就是 JSON 陣列中的第 32 個物件
長度: 8282 字元 | 資訊熵: 2.96 | 候選排名: 第 7 名 | 驗證碼: 58160884
搜尋用 (這個 chunk 的第一行): ## 明志科技大學辦理國外學校學分轉換暨成績轉換參考表 / Ming Chi University of Technology Reference Table 
預覽 (前 400 字元):
## 明志科技大學辦理國外學校學分轉換暨成績轉換參考表 / Ming Chi University of Technology Reference Table for Foreign School Credit and Grade Conversion / 一、國外學校學分轉換參考表Reference Table for Foreign School Credit Conversion

|   區域 area 學分數 Credit |   臺灣 Taiwan |   亞洲 Asia |   澳洲 Australia |   美洲 Americas |   歐盟 European Union |   英國 U.K. |
|---------------------------|---------------|-------------|------------------|--------
- 這是什麼樣的文字？為什麼會這麼長？行政法規／參考對照文件
- 之後做問答檢索時，這麼長的 chunk 可能造成什麼問題？全球多個主要區域與國家的學分對照，以及各國不同的成績評量制度與台灣分數／等第的大型多欄位對照表格，包含大量的數值與國家名稱

**(b) 資訊熵很低的 chunk**
資料檔 (JSON): data/processed/Library_Information/cleaned_A271010023_圖書館管理作業規範_processed.json
閱讀用檔案 (有正常換行): data/interim/Library_Information/cleaned_A271010023_圖書館管理作業規範.md
從第 1713 行開始 (VS Code 中按 Ctrl + G，輸入 1713，即可跳到這一行)
位置: 第 142 個 chunk (從 0 開始數)，也就是 JSON 陣列中的第 143 個物件
長度: 14350 字元 | 資訊熵: 1.21 | 候選排名: 第 1 名 | 驗證碼: 44c345dd
搜尋用 (這個 chunk 的第一行): ## Attachment 5 / Comparison Table of Unit Recommendation Points in Database
預覽 (前 400 字元):
## Attachment 5 / Comparison Table of Unit Recommendation Points in Database

|              |              | Number of Databases Recommended by X Unit - 1 2   | Number of Databases Recommended by X Unit - 3   |   Number of Databases Recommended by X Unit - 4 | 
- 為什麼它的資訊熵這麼低？它對問答檢索有用嗎？ 文字中充滿大量重複的表格標題，表格內包含極多未填寫的空白儲存格，字的資訊密度與詞彙多樣性低，因此資訊熵偏低/未經過結構化清洗、轉化為乾淨的 Markdown 格式或轉換成語意摘要之前，這類文字對問答檢索的幫助極低

## 4. 一個尚未解決的問題 (One Remaining Problem)

> 打開 `data/interim/` 中任一個 `cleaned_*.md` (與 `data/processed/` 的 JSON 內容相同，但有正常換行，比較好讀)，找出一個清洗後**仍然有問題**的 chunk。
> 每個 chunk 從一個 `## ` 標題開始，到下一個 `## ` 標題之前結束。
> 例如：只有標題沒有內文、表格亂掉、中英文沒有對齊、還有殘留的頁首頁尾、斷行造成的多餘空白，或是**清洗造成的錯誤** (誤合併、誤刪除)。
> **不可**使用第 3.4 節的兩個 chunk。

- **檔名** (`cleaned_*.md`)：clean_A232020018_大學部學則.md　**從第 286 行開始** (VS Code 左側的行號)　**標題**：第二章 繳費、註冊、選課 / Chapter 2 Payment of Fees, Registration and Course Selection
- **我是怎麼找到的** (例如：搜尋了什麼、看了哪個檔案)：看了clean_A232020018_大學部學則.md
- **問題 chunk (貼上部分內容)**：

```text
- 第十一條 學生應依規定日期辦理註冊。如因重病、特殊事故或因懷
- 孕、分娩或撫育三歲以下子女引發之事(病)假、產假，經 檢具證明文件於事前請假核准者，得延期註冊，但至多以 兩星期為限。

未經請假或超過准假日期未註冊者，新生如未報准保留入 學資格者則取消入學資格，舊生如未申請休學者即令退

學。 / Article 11 Students shall report to the University for registration on the specified date. If a student takes sick leave or maternity leave due to serious illness, special accidents, pregnancy, childbirth, or caring for children under three years old
```

- **問題是什麼**：出現非預期的行首連字號（- ）、中文詞彙被異常斷開
- **可能的原因** (PDF 本身？Docling 轉換？清洗的正則表示式？切塊規則？)：PDF 原本的排版換行或項目符號被錯誤解析為 - ，且在解析過程中在中文單字間殘留了多餘空白，採用了固定的長度（Token 限制）切塊，導致英文段落未結束就被強制切斷成下一個 Chunk
- **具體的修正方法** (例如：一條規則、一個正則表示式的構想、長度上限)：使用正則表達式清除行首的 -  符號，並移除中文字符之間的空白
- **對問答檢索的影響**：多餘的符號與斷詞會降低向量嵌入的語意品質，導致 RAG 系統無法完整回答關於註冊期限與請假規定的細節

## 5. AI 協作 (AI Collaboration)

- 本次作業的 AI 協作紀錄請見 [`AI_USAGE.md`](AI_USAGE.md) 的「Week 04 / 08」與「Week 09」段落。
- 這次使用 AI 最大的收穫或教訓是 這次使用 AI 最大的收穫或教訓是 在檢索前期的資料前置清洗與切塊策略比想像中更具決定性；AI 的解讀能力高度依賴結構化的正確性，一旦原始文本殘留換行、斷詞或排版錯亂，就會直接導致嵌入向量品質下降並引發檢索失真
