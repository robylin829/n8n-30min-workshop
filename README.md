# n8n 30 分鐘工作坊：作業截止提醒

你同時有好幾門課的作業，哪一份今天就該處理？這堂課用 n8n 把一筆模擬作業分成「優先處理」或「排入計畫」，並用 24 和 25 小時驗證分流。

適合第一次使用 n8n 的大學生。課堂用 n8n Cloud 和內建節點，只需瀏覽器和可用的 n8n 工作區。練習在畫布顯示提醒標籤，使用手動輸入和手動執行。

## 教材

- [學員講義](student-guide.md) 及 [教師版教案](instructor-guide.md)
- [下載可編輯 PowerPoint 教學簡報](slides/n8n-30min-workshop.pptx?raw=true)
- [起始 workflow JSON](workflows/starter.json?raw=true)（已接好觸發和測試資料）
- [完成版 workflow JSON](workflows/completed.json?raw=true)（含 If 與兩條輸出分支）

## 30 分鐘課程

| 時間 | 活動 |
| --- | --- |
| 00:00–05:00 | 概念：認識觸發器、節點與分支 |
| 05:00–12:00 | 示範：建立測試資料，執行流程並查看輸出 |
| **12:00–27:00** | **學員實作：設定 If、標記結果、執行兩組測試** |
| 27:00–30:00 | 同伴驗收：檢查 24 小時和 25 小時的分流 |

課前請登入 [n8n Cloud](https://app.n8n.cloud/) 並確認能建立工作流程。開課前先下載起始 JSON。課堂不需另外串接帳號或申請 API 金鑰。

## 官方參考

[Manual Trigger](https://docs.n8n.io/integrations/builtin/core-nodes/n8n-nodes-base.manualworkflowtrigger/) · [Edit Fields (Set)](https://docs.n8n.io/integrations/builtin/core-nodes/n8n-nodes-base.set/) · [If](https://docs.n8n.io/integrations/builtin/core-nodes/n8n-nodes-base.if/) · [匯入與匯出](https://docs.n8n.io/build/manage-workflows/export-and-import/)
