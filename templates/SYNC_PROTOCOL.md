# 同步協議封包範本 (SYNC_PROTOCOL)

---
id: "SYNC-PAYLOAD-{YYMMDD}-{HHMM}"
type: "payload"
sender: "{your_name_or_team}"
receiver: "{target_name_or_team}"
action_type: "{update_task | create_task | broadcast | conflict_alert}"
timestamp: "{ISO_8601_Time}"
---

## 📌 意圖摘要 (Summary)
[在此用一句話說明此封包的目的，例如：提交功能模組的開發日誌，請求合併進度]

## 🛠 異動與負載 (Payload Details)

### 更新的主任務 (Main Task Updated)
- Task ID: `{Task_ID}`
- New Status: `{done | blocked}`

### 執行結論與關鍵洞察 (Insights)
1. 發現...
2. 決定...
3. (Optional) 請求協助區塊：目前卡在...

## 🔗 檢附來源 (References)
- [Local Log: WL_...](../../workmgr/work-logs/WL_...)
- [Commit: add_feature_xyz]
