# 🛠 團隊工具使用與對齊指引 (Team Tools Usage & Sync Guide)

> **說明**：本檔案規範了團隊在實驗期間的具體操作格律。在 AI 賦能組織中，「格式就是戰鬥力」，因為它是 AI 能夠精準介入的標準化介面。

---

## 1. 📂 Git 與命名空間 (Namespace)
我們使用 Git 作為單一事實來源 (SSOT)，並透過「來源碼」區隔不同的任務與日誌脈絡。

*   **三碼來源碼 (Namespace)**：
    *   `HHH` (Global)：全域最高裁決層。
    *   `SHP` (SyncHub Team)：團隊實驗項目層。
    *   `WUL` (Wuulong)：成員個人沙盒層 (Sandbox)。
*   **ID 格式**：`T{YYMMDD}-{來源碼}{序號}` (例如：`T260303-SHP01`)。
*   **Commit 規範**：每次 Commit 應附帶相關任務 ID。格式：`[任務ID] 動詞: 描述`。

---

## 2. ⌨️ 快速指令介面 (Justfile Shortcuts)
為了降低操作摩擦，團隊統一使用 `just` 指令作為與系統（及 AI）互動的介面。

| 功能 | 語法 (以 SHP 為例) | 說明 |
| :--- | :--- | :--- |
| **新增任務** | `just at SHP "任務名" "高"` | 自動生成 ID 並插入帳本 |
| **結案任務** | `just dn SHP ID` | 標示完成、移動歸檔並同步日誌 |
| **紀錄日誌** | `just lg SHP "紀錄"` | 快速在對應層級日誌寫入經歷 |

---

## 3. 🔄 非同步對合機制 (Inbox / Outbox)
團隊成員與 SyncHub (團隊 AI) 之間不直接修改對方的核心檔案，而是透過「拋接」進行協作。

*   **個人 Outbox 提交**：成員完成任務後，將封包 (Payload) 放入 `members/{name}/workmgr/outbox/`，代表「請求團隊採納」。
*   **團隊 Inbox 接收**：SyncHub 定期掃描所有成員的 `outbox/` 並匯總至團隊級別的 `inbox/`。
*   **對合衝突處理**：若 AI 發現不同成員對同一任務有衝突見解，會發布警告於 `task-reports` 並標註 `Blocked`。

---

## 4. 📝 Markdown 寫作規範
*   **相對路徑**：檔案連結必須使用相對路徑（如 `../task/TASKS.md`）。
*   **三層勾稽**：每日工作日誌 (Wlog) 最後必須包含「三層結構勾稽校準」，確認個人、專案、全域進度是否同步。
*   **AI 協作宣告**：所有使用 AI 生成或潤飾的文件，應於文末添加 AI 協作聲明。

---

## 5. 🧠 外部知識庫 (NotebookLM)
*   **定位**：NotebookLM 作為團隊的「動態手冊」與「脈絡查詢引擎」。
*   **同步頻率**：每當 `rules/` 或 `docs/` 有重大更新並結案時，應重新匯出並上傳至 NotebookLM。
*   **查詢原則**：新成員加入時，應優先向 NotebookLM 詢問運作規則，而非反覆詢問人類負責人。

---
*Last Updated: 2026-03-03 | SyncHub Prototype Standard v1.1*
