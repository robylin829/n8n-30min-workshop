# n8n 30 分鐘工作坊：信件整理

收件匣裡的作業通知、社團活動和其他信件混在一起。這堂課用 n8n 讀取一封模擬信件的主旨。主旨含「作業」就標為「課務」，其他信件標為「一般」。

適合第一次使用 n8n 的大學生。課堂用 n8n Cloud 和內建節點，只需瀏覽器和可用的 n8n 工作區。實作在 n8n 畫布顯示分類結果，教師版教案另附 Gmail 標籤的延伸方向。

## 教材

- [學員講義](student-guide.md) 及 [教師版教案](instructor-guide.md)
- [下載可編輯 PowerPoint 教學簡報](slides/n8n-30min-workshop.pptx?raw=true)
- [起始 workflow JSON](workflows/starter.json?raw=true)（已接好觸發和測試資料）
- [完成版 workflow JSON](workflows/completed.json?raw=true)（含 If 與兩條輸出分支）

## 30 分鐘課程

| 時間 | 活動 |
| --- | --- |
| 00:00–05:00 | 概念：認識觸發器、節點與分支 |
| 05:00–12:00 | 示範：建立模擬信件，執行流程並查看主旨 |
| **12:00–27:00** | **學員實作：設定主旨關鍵字、加上分類欄位並測試兩封信** |
| 27:00–30:00 | 同伴驗收：核對「課務」與「一般」兩種結果 |

單次上課可在課前開通 [n8n Cloud](https://app.n8n.cloud/) 的 14 天免費試用，無需信用卡，試用期滿後若要繼續使用需付費。若學校已架設免費的 Community Edition，也可以在該環境匯入同一份教材。課前先確認可以建立工作流程並下載起始 JSON。[Cloud 試用說明](https://support.n8n.io/article/how-do-i-cancel-my-trial) · [Community Edition 說明](https://support.n8n.io/article/can-i-get-n8-n-for-free)

## 官方參考

[Manual Trigger](https://docs.n8n.io/integrations/builtin/core-nodes/n8n-nodes-base.manualworkflowtrigger/) · [Edit Fields (Set)](https://docs.n8n.io/integrations/builtin/core-nodes/n8n-nodes-base.set/) · [If](https://docs.n8n.io/integrations/builtin/core-nodes/n8n-nodes-base.if/) · [匯入與匯出](https://docs.n8n.io/build/manage-workflows/export-and-import/)
