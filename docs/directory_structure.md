# 目錄結構設計說明 (Directory Structure)

本文件說明 `synchub-prototype` 專案目錄結構的設計理念與具體用途。本專案以「碎形邏輯」與「非同步對合 (Async Sync)」為核心，將 GitHub 打造為個人 AI 與團隊 AI (SyncHub) 共舞的基礎設施。

## 🌳 完整目錄結構樹

```text
events/synchub-prototype/
├── workmgr/                     # 🏢 團隊層級的運作管理區 (Team Context)
│   ├── roadmap/                 # 🗺️ 團隊發展藍圖與長期目標
│   ├── task/                    # 🎯 團隊共同任務追蹤與狀態
│   ├── work-logs/               # 📅 團隊對合報告 (Team Daily/Weekly Summary)
│   ├── inbox/                   # 📥 [團隊收件匣] 成員個人透過其 outbox 發布上來的合併/對合請求區
│   └── outbox/                  # 📤 [團隊寄件匣] 團隊發布給「所有成員」的公共廣播、全局任務或最新協議公告
│
├── members/                     # 👥 成員個人空間 (Individual Contexts)
│   └── _template/               # 👤 個人環境預設範本
│       ├── workmgr/             # 🏠 個人的任務與日誌區 (PA Sandbox 操作區)
│       │   ├── task/            # 個人的任務清單與子任務狀態
│       │   └── work-logs/       # 個人每日工作日誌 (草稿或內部思考區)
│       └── sync/                # 🔄 個人對合通訊區 (與 SyncHub 介接處)
│           ├── inbox/           # 📥 [個人收件匣] 團隊 (SyncHub) 派發的專屬任務、來自團隊 outbox 的廣播，或對合反饋
│           └── outbox/          # 📤 [個人寄件匣] 裁決後準備提交給團隊 (進入團隊 inbox) 的完成任務報告或重要決策
│
├── docs/                        # 📚 專案說明與架構
│   ├── architecture.md          # 說明 SyncHub 非同步對合 (Inbox/Outbox) 運作流程與系統設計
│   └── directory_structure.md   # [本文件] 說明目錄結構與各區塊功能
├── rules/                       # ⚖️ 團隊運作「憲法」與「度量衡」
│   ├── TEAM_HANDBOOK.md         # 團隊運作說明書
│   └── TEAM_TOOLS_GUIDE.md      # 團隊工具使用與對齊指引 (含 Inbox/Outbox 檔案格式規範)
├── templates/                   # 📝 標準化範本庫
│   ├── SYNC_PROTOCOL.md         # 傳送至 inbox/outbox 的標準訊息封包範本 (JSON/Markdown 混合)
│   ├── TASK_TEMPLATE.md         # 標準任務範本
│   └── WLOG_TEMPLATE.md         # 個人工作日誌範本
│
├── AIQA/                        # (舊有資料保留區) 存放先前的問答紀錄
└── README.md                    # 🌟 專案入口點
```

## 🧠 設計理念與運作說明

### 1. 碎形對稱性 (Fractal Symmetry)
本架構貫徹「企業是由個體組成的碎形」概念。
團隊層級擁有 `workmgr/`（包含 roadmap, task, work-logs），而個人層級 (`members/.../workmgr/`) 也擁有相同的結構。
這種對稱性讓個人 AI 沙盒 (PA Sandbox) 運作的資料，能以相同的邏輯被團隊 AI (SyncHub) 讀取與整合。

### 2. 非同步對合 (Inbox / Outbox 機制)
團隊與個人的資訊交換不是直接修改彼此的檔案（避免 Git 衝突與權責混亂），而是透過「收發室」的概念進行拋接：
- **上傳通道 (Bottom-Up)**：個人在自己的 `workmgr` 完成工作並裁決後，將封包放入 `sync/outbox/`，準備被團隊的 `inbox/` 抓取並整併到團隊的 `workmgr` 中。
- **下達通道 (Top-Down)**：團隊全局決議或新指派任務會發布到團隊的 `outbox/`，然後被派發到各個成員的 `sync/inbox/` 供個人 AI 去消化成個人的任務。

### 3. 單一事實來源 (SSOT) 具象化
所有討論與成果最終都會落地為這套目錄結構中的文字檔 (Markdown/YAML)。
- `rules/` 目錄像是系統的硬性約束（協定）。
- `templates/` 確保了訊息拋接過程中的格式一致性，降低 AI 的解析成本。
