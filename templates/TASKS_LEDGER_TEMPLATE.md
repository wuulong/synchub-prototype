# 📋 任務總帳本範本 (TASKS_LEDGER_TEMPLATE)

> **操作說明**：本檔案取代單張任務卡機制。無論是團隊的 `workmgr/task/TASKS.md` 還是個人的 `members/{name}/workmgr/task/TASKS.md`，皆使用此帳本進行集中式清單管理。團隊 SyncHub 將會定期掃描並對合本地 `[ ]` 與 `[x]` 狀態。

> **Retention Policy**: Completed items are moved to `## ✅ 已完成 (Archive)` with completion dates. 
> **ID System**: 每項任務使用 sequence-based ID `T{YYMMDD}-{NN}` (T prefix for Todo, followed by date and sequence)。

---

## 🚀 當前執行 (Ongoing)
*範例格式：`- [ ] [任務ID] **主標題** [優先級:高中低] @執行者`*

- [ ] [T26XXXX-01] **第一項核心實作** [優先級:高] @Username
    - *任務內容*: 進行某某原型的開發與設計驗證。
    - *對合路徑 (Sync Inbox)*: [若需要團隊對合，請在此標明預計送交的 Outbox Payload ID]
    - *進度*: 目前完成雛型階段。
    - *子任務*:
        - [x] 子項目 A 完成
        - [ ] 子項目 B 待處理

- [ ] [T26XXXX-02] **第二項待辦** [優先級:中] @Username
    - *任務內容*: 撰寫基礎架構說明。

## 📥 待處理收納 (Backlog)
- [ ] [T26XXXX-03] (未來擴展) 自動化測試腳本建置 [優先級:低] @Unassigned
- [ ] [T26XXXX-04] (Idea) 嘗試導入某某新技術驗證 [優先級:低] 

## ⏳ 等待回應 (Blocked/Waiting)
- [ ] [T26XXXX-05] 等待外部 API 權限開通，暫時擱置 [優先級:高] @Username

## ✅ 已完成 (Archive)
- [x] [T26XXXX-00] **專案骨架初始化完成** [優先級:高] @Username [2026-XX-XX]
    - *進度*: 已將架構推陳至 Git 根目錄。
