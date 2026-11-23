# 學員講義：作業截止提醒

你會把一筆尚未到期的作業標記成「優先處理」或「排入計畫」。剩餘時間用 `hoursLeft` 表示，每次執行處理一筆作業。

## 課前準備

1. 登入 [n8n Cloud](https://app.n8n.cloud/)，確認可以開啟工作流程編輯器並建立新 workflow。
2. 下載 [起始 workflow JSON](workflows/starter.json?raw=true)，課堂卡關時備用。

## 15 分鐘實作

### 0–4 分鐘｜建立測試資料

1. 建立新 workflow，命名為「作業截止提醒」，新增 **Manual Trigger**（在搜尋結果中也可能顯示為 **Trigger manually**）。
2. 接上 **Edit Fields (Set)**，命名為「模擬作業」。在 **Manual Mapping** 新增下列欄位。

   | 欄位名稱 | 型別 | 固定值 |
   | --- | --- | --- |
   | `assignment` | String | `資料分析作業` |
   | `hoursLeft` | Number | `24` |

3. 點畫布上的 **Execute workflow**。開啟「模擬作業」的 **Output**，確認兩個欄位都有值。

如果四分鐘內還沒看到資料，開啟一個空白 workflow。從右上角 `…` 選 **Import from File**，匯入 [起始 JSON](workflows/starter.json?raw=true)，接著做下一段。

### 4–11 分鐘｜設定條件和輸出

1. 從「模擬作業」接上 **If**。將左側值切成 **Expression**，輸入 `{{ $json.hoursLeft }}`，也可以從 **Input** 把 `hoursLeft` 拖進左側欄位。
2. 選擇 **Number** 下的 **is less than or equal to**（小於或等於），右側固定值輸入 `24`。
3. 從 `true` 出口新增 **Edit Fields (Set)**，命名「優先處理」。用 **Manual Mapping** 新增 String 欄位 `priority`，固定值填 `優先處理`。開啟 **Include Other Input Fields**，保留作業名稱與剩餘時間。
4. 從 `false` 出口新增另一個 **Edit Fields (Set)**，命名「排入計畫」。用相同方式新增 `priority`，固定值填 `排入計畫`，並保留輸入欄位。

### 11–15 分鐘｜跑兩筆測試

在「模擬作業」修改 `hoursLeft`。每次改值後回畫布重新執行整條 workflow，先看 If 的分支，再打開該分支的終點查看 `priority`。

| `hoursLeft` | If 有資料的出口 | 終點的 `priority` |
| --- | --- | --- |
| `24` | `true` | `優先處理` |
| `25` | `false` | `排入計畫` |

完成後儲存 workflow。提早完成可把門檻改成 `48`，先猜 48 和 49 小時會走哪條分支，再執行驗證。

## 3 分鐘同伴驗收

兩人一組，輪流展示同一條 workflow 的兩次執行結果，或現場改值重跑。確認 24 小時走 `true` 且輸出 `優先處理`，25 小時走 `false` 且輸出 `排入計畫`。用一句話說明 24 小時為什麼會被列為優先。

## 卡關時可以看哪裡

| 現象 | 檢查方式 |
| --- | --- |
| If 找不到 `hoursLeft` | 先執行整條流程。確認前一個節點有輸出，欄位大小寫一致。 |
| If 顯示型別錯誤 | 測試資料的 `hoursLeft` 必須選 Number。If 左側用 Expression，右側填固定數字。 |
| 改了數值，結果沒有變 | 檢查「模擬作業」是否有釘選資料。有的話先取消釘選，再執行整條流程。 |
| 24 小時走到 `false` | 檢查條件是否為「小於或等於」，包含 24 這個值。 |
| 分支有跑，但輸出只剩 `priority` | 在終點 Edit Fields 開啟 Include Other Input Fields。 |

課後可匯入 [完成版 JSON](workflows/completed.json?raw=true) 對照。這個模型使用已知的剩餘時數。若要做成日常提醒，可再接排程和作業截止日期來源。
