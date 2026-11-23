# 學員講義：社團器材報修分流

用一張表單收集器材名稱和使用狀況。送出「無法使用」時，頁面顯示「優先處理」。送出「仍可使用」時，頁面顯示「一般報修」。

## 上課前

看 [環境建置指南](setup.md)，登入 Cloud 或教師已架好的 n8n，確認可以建立 workflow。下載並解壓教材，讓 `workflows/starter.json` 隨手可用。

## 15 分鐘實作

### 0–4 分鐘｜建立報修表單

1. 新建工作流程。新增 **n8n Form Trigger**（搜尋 **On form submission**），將 **Form Title** 填為「社團器材報修」，**Form Description** 填「請用模擬資料練習」。
2. 新增下面兩項 **Form Elements**，都設為必填。若介面有 **Custom Field Name**，可從 **Add Attributes** 加入。較早版本直接在 **Field Name** 填英文欄位名。

   | Label（顯示名稱） | Custom Field Name 或 Field Name | 類型 | 選項 |
   | --- | --- | --- | --- |
   | 器材名稱 | `equipment` | Text Input | 自行輸入 |
   | 使用狀況 | `status` | Dropdown | `無法使用`、`仍可使用` |

3. 把 **Respond When** 選為 **Workflow Finishes**。點畫布的 **Execute workflow**，在測試表單填「投影機、無法使用」並送出。回畫布打開 Form Trigger 的 **Output**，找到 `equipment` 和 `status`。

如果第 4 分鐘還沒看到輸出，在空白 workflow 用右上角 **… → Import from File** 匯入 [起始版 JSON](workflows/starter.json?raw=true)，接著做下一段。起始版只有表單，送出時只會顯示通用確認頁。

### 4–11 分鐘｜設定分支與完成頁

1. 從表單接一個 **If**。左側切為 **Expression**，輸入 `{{ $json.status }}`，也可以拖入測試輸出的 `status`。選 **String → is equal to**，右側固定填 `無法使用`。
2. 從 `true` 接一個 **n8n Form**。將 **Page Type** 選 **Form Ending**，**On n8n Form Submission** 選 **Show Completion Screen**，**Completion Title** 填「優先處理」。
3. 從 `false` 接另一個 **n8n Form**，使用相同設定，**Completion Title** 填「一般報修」。

### 11–15 分鐘｜互測

每筆測試開始前，回編輯器點一次 **Execute workflow**，再到開啟的表單填寫並送出。測試網址是 **Test URL**。每次送出後確認瀏覽器結果，並回 n8n 檢查哪個終點節點有執行。

| 器材名稱 | 使用狀況 | If 分支 | 完成頁標題 |
| --- | --- | --- | --- |
| 投影機 | 無法使用 | `true` | 優先處理 |
| 麥克風 | 仍可使用 | `false` | 一般報修 |

## 最後 3 分鐘驗收

同伴在同一台電腦輪流送出兩筆或展示既有結果。兩種完成頁都正確，且能指出 `If` 是用 `status` 判斷，就完成實作。

| 卡關狀況 | 檢查方式 |
| --- | --- |
| 表單網址出現 404 或未註冊 | 回畫布點 **Execute workflow**，再打開當次的 **Test URL**。 |
| 送出只看到通用確認頁 | 確認 **Respond When** 是 **Workflow Finishes**，並用畫布的 **Execute workflow** 跑整條流程。 |
| 兩次都走 `false` | 檢查表單輸出欄位是否叫 `status`，下拉選項和右側比較值是否都拼成「無法使用」。 |
| 本機表單在另一台電腦打不開 | 在開著 n8n 的同一台電腦換人填寫。 |

課後可匯入 [完成版 JSON](workflows/completed.json?raw=true) 對照，或另存自己的工作流程，保留日後匯入的檔案。[n8n 表單測試說明](https://docs.n8n.io/integrations/builtin/core-nodes/n8n-nodes-base.formtrigger/#build-and-test-workflows)
