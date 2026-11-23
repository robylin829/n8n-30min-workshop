# 課前環境建置

30 分鐘從 n8n 編輯器已可使用時開始。工作區開通、安裝和第一次登入都放在課前。

| 使用情況 | 選擇 | 課前確認 |
| --- | --- | --- |
| 單次課程、教室電腦安裝權限不一 | **n8n Cloud** | 能登入、開啟編輯器，並用 Test URL 送出一筆。 |
| 教師或學校已有可用的 n8n Docker 環境 | **Docker 自架** | 確認學生使用的網址、登入方式，以及報修表單可以送出。 |

## 方式一｜n8n Cloud

1. 在 [n8n Cloud](https://app.n8n.cloud/) 開通試用或登入教師指定的工作區。標準試用 14 天，無需信用卡。試用期滿後繼續使用須付費。
2. [下載教材 ZIP](https://github.com/robylin829/n8n-30min-workshop/archive/refs/heads/main.zip) 並解壓。在工作區建立空白 workflow，從右上角 **… → Import from File** 選擇 `workflows/starter.json`。
3. 點 **Execute workflow**，確認測試表單可以開啟並送出一筆。若瀏覽器未開新分頁，可到 Form Trigger 複製 **Test URL**，在同一瀏覽器開啟。[Cloud 試用說明](https://support.n8n.io/article/how-do-i-cancel-my-trial) · [官方定價](https://n8n.io/pricing/)

## 方式二｜使用已架好的 Docker n8n

1. 教師在課前啟動 Docker 內的 n8n，確認網頁編輯器可登入、重啟後工作流程能保留。本機使用時請開啟該機器的 n8n 網址，例如 `http://localhost:5678`。
2. 下載並解壓同一個教材 ZIP。匯入 `workflows/starter.json`，點 **Execute workflow** 並送出報修表單。課堂中的每筆測試都先回畫布重新執行。
3. 使用 `localhost` 時，兩人請在同一台電腦輪流操作。如果 Windows 的 WSL 2 或其他 Docker 後端目前無法啟動，本次課可改用 Cloud，Docker 建置留到課前或另一次練習。[n8n Docker Compose 文件](https://docs.n8n.io/deploy/host-n8n/install-options/install-using-docker-compose/) · [Docker Desktop Windows 系統需求](https://docs.docker.com/desktop/setup/install/windows-install/)

## 進教室前的檢查

- 學生能登入、建立 workflow、開啟測試表單。
- 教師用完成版送出兩筆，分別核對「優先處理」和「一般報修」。
- 同伴測試只需用模擬器材資料。課上使用 **Test URL**，每次測試前重新按 **Execute workflow**。[n8n 表單測試文件](https://docs.n8n.io/integrations/builtin/core-nodes/n8n-nodes-base.formtrigger/#build-and-test-workflows)
