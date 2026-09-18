# 題庫目錄（多位老師共編）

這個資料夾是「練習頁 → 題組測驗 → 從題庫目錄載入」用的 GitHub 題庫。
練習頁只要拿到 `catalog.json` 的 **raw 網址**，就會先載目錄、再讓使用者選題組載入。

## 資料夾結構

```
catalog.json            ← 目錄（列出有哪些題組）
banks/
  loops-basic.txt       ← 各題組檔（沿用原本的 .txt 格式）
  if-intro.txt
```

## catalog.json 格式

一個陣列，每個元素是一個題組：

```json
[
  { "name": "迴圈基礎題組", "category": "迴圈", "url": "banks/loops-basic.txt" },
  { "name": "條件判斷入門", "category": "條件", "url": "banks/if-intro.txt" }
]
```

- `name`：下拉選單顯示的題組名稱（必填）
- `category`：分類，顯示成 `[分類] 名稱`（可留空）
- `url`：題組檔位置。**相對路徑**（相對於 catalog.json）即可，整個 repo 搬家也不用改；也可放完整 raw 網址。

## 題組 .txt 格式（與原本相同）

```
題目：印出 1 到 N
說明：讀入一個正整數 N，依序印出 1 到 N，每個數字一行。

筆數：2
輸入1_1：3
輸出1：1
2
3
分數1：50
輸入2_1：5
輸出2：1
2
3
4
5
分數2：50
---
題目：下一題…
```

- `輸入N_M：` = 第 N 筆測資的第 M 行輸入（多行輸入就 `_1`、`_2`…）
- `輸出N：` 之後可以跨多行，直到下一個關鍵字
- 題與題之間用 `---` 分隔

## 取得 raw 網址

在 GitHub 開一個 repo（例如 `question-bank`），把這些檔案放進去後，點開 `catalog.json` →
按右上角 **Raw** → 複製網址，形如：

```
https://raw.githubusercontent.com/<你的帳號>/question-bank/main/catalog.json
```

把這個網址貼到練習頁「開始測驗設定 → 題庫目錄網址」，按「載入目錄」即可。
（網址會記在瀏覽器，下次自動帶入。）

## 多位老師共編

- **直接共編**：把其他老師加為 repo 的 collaborator，大家都能直接 push。
- **審稿制**：老師各自開 branch → 發 Pull Request，由你合併後才進 `main`。
- 新增題組 = 在 `banks/` 放一個 `.txt`，並在 `catalog.json` 加一行。
- 所有修改都有版本歷史，改壞了可隨時還原。
