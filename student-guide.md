# 學員講義：信件整理

你會依主旨把信件標為「課務」或「一般」。每次執行處理一封模擬信件，主旨存在 `subject` 欄位。

## 課前準備

1. 登入教師指定的 n8n 工作區。若使用 [n8n Cloud](https://app.n8n.cloud/)，可在課前開通 14 天免費試用，無需信用卡。確認能開啟編輯器並建立新 workflow。[Cloud 試用說明](https://support.n8n.io/article/how-do-i-cancel-my-trial)
2. 下載 [起始 workflow JSON](workflows/starter.json?raw=true)，課堂卡關時備用。

## 15 分鐘實作

### 0–4 分鐘｜建立模擬信件

1. 建立新 workflow，命名為「信件整理」，新增 **Manual Trigger**（在搜尋結果中也可能顯示為 **Trigger manually**）。
2. 接上 **Edit Fields (Set)**，命名為「模擬信件」。在 **Manual Mapping** 新增下列欄位。

   | 欄位名稱 | 型別 | 固定值 |
   | --- | --- | --- |
   | `subject` | String | `資料分析作業繳交通知` |

3. 點畫布上的 **Execute workflow**。開啟「模擬信件」的 **Output**，確認讀得到 `subject`。

如果四分鐘內還沒看到資料，開啟一個空白 workflow。從右上角 `…` 選 **Import from File**，匯入 [起始 JSON](workflows/starter.json?raw=true)，接著做下一段。

### 4–11 分鐘｜設定條件和輸出

1. 從「模擬信件」接上 **If**。將左側值切成 **Expression**，輸入 `{{ $json.subject }}`，也可以從 **Input** 把 `subject` 拖進左側欄位。
2. 選擇 **String** 下的 **contains**（包含），右側固定值輸入 `作業`。
3. 從 `true` 出口新增 **Edit Fields (Set)**，命名「課務」。用 **Manual Mapping** 新增 String 欄位 `label`，固定值填 `課務`。開啟 **Include Other Input Fields**，保留原本的信件主旨。
4. 從 `false` 出口新增另一個 **Edit Fields (Set)**，命名「一般」。用相同方式新增 `label`，固定值填 `一般`，並保留主旨。

### 11–15 分鐘｜測試兩封信

在「模擬信件」修改 `subject`。每次改值後回畫布重新執行整條 workflow，先看 `If` 的分支，再打開該分支的終點查看 `subject` 和 `label`。

| `subject` | `If` 有資料的出口 | 終點的 `label` |
| --- | --- | --- |
| `資料分析作業繳交通知` | `true` | `課務` |
| `系學會迎新聚餐通知` | `false` | `一般` |

完成後儲存 workflow。提早完成可測試「期中考教室異動通知」。這封信也是課務信件，但目前會進「一般」。試著在 `If` 加上包含「期中考」的條件，並選擇 **OR**，再重跑三封信。

## 3 分鐘同伴驗收

兩人一組，輪流展示同一條 workflow 的兩次執行結果，或現場改主旨重跑。確認作業通知標為「課務」，迎新通知標為「一般」。用一句話說明 `If` 是根據哪個欄位和關鍵字分流。

## 卡關時可以看哪裡

| 現象 | 檢查方式 |
| --- | --- |
| `If` 找不到 `subject` | 先執行整條流程。確認前一個節點有輸出，欄位大小寫一致。 |
| 作業通知走到 `false` | 確認左側用 Expression，條件為 String 的 contains，右側固定寫 `作業`。 |
| 改了主旨，結果沒有變 | 檢查「模擬信件」是否有釘選資料。有的話先取消釘選，再執行整條流程。 |
| 分支有跑，但輸出只剩 `label` | 在終點 Edit Fields 開啟 Include Other Input Fields。 |

課後可匯入 [完成版 JSON](workflows/completed.json?raw=true) 對照。要將分類用於信箱，可參考 [Gmail 節點的 Add Label 操作](https://docs.n8n.io/integrations/builtin/app-nodes/n8n-nodes-base.gmail/message-operations/#add-label-to-a-message)。
