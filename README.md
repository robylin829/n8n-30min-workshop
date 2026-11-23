# n8n 30 分鐘工作坊：社團器材報修分流

兩位同學用同一張報修表單，分別回報「無法使用」和「仍可使用」。n8n 在送出時執行，並在瀏覽器顯示「優先處理」或「一般報修」。

適合第一次用 n8n 的大學生。實作使用 n8n 內建表單和條件節點，只需填寫模擬報修資料。

## 下載與課前準備

- [下載整套教材 ZIP](https://github.com/robylin829/n8n-30min-workshop/archive/refs/heads/main.zip)
- [環境建置指南](setup.md)（n8n Cloud 與已架好的 Docker 自架環境）
- [教師版教案](instructor-guide.md) · [學員講義](student-guide.md) · [可編輯 PowerPoint](slides/n8n-30min-workshop.pptx?raw=true)
- [起始版 JSON](workflows/starter.json?raw=true)（報修表單）· [完成版 JSON](workflows/completed.json?raw=true)（表單、分支和兩個結果頁）

**單次上課建議用 Cloud。** 學生課前開好工作區並登入，課堂下載 JSON 後即可匯入。若教室已有透過 Docker 架好的 n8n，可使用同一套教材。

## 30 分鐘課程

| 時間 | 活動 |
| --- | --- |
| 00:00–05:00 | 概念：表單送出如何觸發報修分流 |
| 05:00–12:00 | 示範：建立表單並查看一筆回覆 |
| **12:00–27:00** | **學員實作：建立表單、分支與結果頁，各送出兩種測試** |
| 27:00–30:00 | 同伴驗收：核對兩種完成頁與 n8n 執行路徑 |
