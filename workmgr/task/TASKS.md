# 📋 任務總帳本 (TASKS_LEDGER)

> **操作說明**：本檔案取代單張任務卡機制。無論是團隊的 `workmgr/task/TASKS.md` 還是個人的 `members/{name}/workmgr/task/TASKS.md`，皆使用此帳本進行集中式清單管理。團隊 SyncHub 將會定期掃描並對合本地 `[ ]` 與 `[x]` 狀態。

> **Retention Policy**: Completed items are moved to `## ✅ 已完成 (Archive)` with completion dates. 
> **ID System**: 每項任務使用序列號 `T{YYMMDD}-{來源碼}{序號}`。
>   - **來源碼 (Namespace)**: 團隊任務使用專案縮寫 (如 `SHP`)；個人沙盒任務使用成員縮寫 (如 `WUL`)。
>   - **序號**: 兩位數序列號 `01`, `02`...。
> **Default Priority**: 若未特別標註，任務預設優先級為 `[優先級:中]`。

---

## 🚀 當前執行 (Ongoing)
- [ ] [T260303-SHP05] **成員自選一個對自己有意義，或是對團隊有意義的極小 task, 並開展成 task report 並完成** [優先級:中] @Antigravity
*範例格式：`- [ ] [任務ID] **主標題** [優先級:高中低] @執行者`*

- [ ] [T260303-SHP04] **成員自我管理實驗：更新個人 TASKS.md** [優先級:中] @Team
    - *任務內容*: 成員在自己的個人目錄 `members/{name}/workmgr/task/TASKS.md` 中給自己設定一個任務，並標示已完成，以練習個人沙盒中的任務操作。
    - *對合路徑 (Sync Inbox)*: [等待成員個人 TASKS.md 更新]
    - *進度*: 準備開始
- [ ] [T260303-SHP03] **成員建立自己工作目錄與 commit 確認** [優先級:高] @Team
    - *任務內容*: 成員成功建立個人工作目錄（從 `_template` 複製），並進行首次 commit 以確認編輯與推送權限正常。
    - *對合路徑 (Sync Inbox)*: 不適用
    - *進度*: 準備開始
- [ ] [T260303-SHP02] **成員理解度確認** [優先級:中] @Team
    - *任務內容*: 成員根據文件，是否能基本了解運作的方式，可以請在頻道回覆，不可以請在頻道提出問題。
    - *對合路徑 (Sync Inbox)*: [等待頻道回覆]
    - *進度*: 等待回饋
- [ ] [T260303-SHP01] **設定 github 編輯權限** [優先級:中] @Wuulong
    - *任務內容*: 為團隊成員設定 GitHub 儲存庫的編輯權限，確保成員可以進行後續的對合操作與推送。
    - *對合路徑 (Sync Inbox)*: 不適用
    - *進度*: 準備開始
- [ ] [T260302-SHP02] **團隊成員已經 check-out 目前的團隊 repo** [優先級:中] @Team
    - *任務內容*: 確保所有參與實驗的團隊成員，皆能夠成功 `git clone` 並配置好 `synchub-prototype` 本地開發環境。建立每位成員專屬的 `members/{name}/` 個人空間。
    - *對合路徑 (Sync Inbox)*: [TR_260302-SHP02](../task-reports/TR_260302-SHP02.md)
    - *進度*: 進行中 (In-Progress)。已展開任務報告並建立成員 Onboarding 清單。

## 📥 待處理收納 (Backlog)

## ⏳ 等待回應 (Blocked/Waiting)

## ✅ 已完成 (Archive)
- [x] [T260302-SHP01] **專案骨架初始化完成** [優先級:高] @Antigravity [2026-03-02]
    - *進度*: 已將架構推陳至 Git 根目錄。
