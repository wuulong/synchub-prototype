# SyncHub 系統架構與對合機制 (Architecture)

## 1. 系統設計理念

SyncHub 旨在解決團隊擴編與個人代理 (Personal Agent, PA) 介入後產生的「資訊孤島」與「語意衝突」。
我們捨棄即時通訊軟體 (如 LINE, Discord) 中的發散討論作為真相來源，轉而採用 **Git 檔案系統 + Inbox/Outbox 非同步機制** 來設計底層的通信框架。

## 2. 脈絡對合 (Context Sync) 流程

這是一個典型的「個人 <-> 團隊」雙向資訊循環：

### 2.1 團隊派發 (Team -> Personal)
1. **觸發點**：團隊 (或團隊 Agent) 生成了需廣播全局的新政策或新任務指派。
2. **傳送**：檔案被放入團隊的 `workmgr/outbox/`（或複製到成員專屬的 `members/{name}/sync/inbox/`）。
3. **吸收**：成員的個人代理程式讀取 inbox，將其轉換為內部的 `workmgr/task/` 安排。

### 2.2 個體提交 (Personal -> Team)
1. **內部琢磨**：個人在 `members/{name}/workmgr/` 中建立打草稿，與自己的 PA 進行測試與實驗（PA Sandbox）。
2. **裁決與打包**：個人確認成果後，將正式的日誌或任務狀態打包放入自己的 `sync/outbox/`（或直接推送到團隊的 `workmgr/inbox/`）。
3. **完成通訊**：個人放出的訊息等同於加上了「人類裁決確認」的電子簽章。

### 2.3 團隊融合與對合 (Team Merging)
1. **自動掃描**：團隊的 SyncHub Agent 定期掃描 `workmgr/inbox/` 的內容。
2. **衝突比對**：解析各個 JSON/YAML/Markdown Payload，檢查團隊資源或語意是否有相衝。
3. **落地**：產出統整後的昨日進度 (Team Summary)，放到 `workmgr/work-logs/`，並更新整體的 `workmgr/task/` 供大家拉取最新狀態。

## 3. 將 GitHub 作為唯一真相來源 (SSOT)

- Git 的每一個 commit 代表著一次狀態快照。
- 所有 AI (含 PA 與 SyncHub) 都依託於 Pull/Push 機制。當發生極端衝突時，人類管理者可以透過 Git History 追蹤為何 AI 做出了錯誤的收斂與對合。
