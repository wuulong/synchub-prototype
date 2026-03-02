# 團隊 AI 協作中樞實驗計畫 (SyncHub Prototype)

![SyncHub Logo](https://img.shields.io/badge/SyncHub-Prototype-blue) ![Status](https://img.shields.io/badge/Status-Experimental-orange)

> 「企業的每一項決策、每一行程式碼、每一份報告，最終都源於某位特定個體的智力產出。」  
> —— 《演化路徑：企業賦能的碎形邏輯：個人為基，團隊為原型》第 0 章

## 🌟 專案目標

本專案旨在驗證 **「超小型團隊 (Nano-Squad) 如何透過 SyncHub 實現無痛脈絡對合 (Context Sync)」**。
我們將 GitHub 視為團隊的單一真相來源 (SSOT)，結合非同步的對合機制 (Inbox / Outbox)，確保個人 AI 沙盒與團隊大腦之間的資訊能暢通無阻、並自動進行衝突對齊。

## 📂 核心架構運作邏輯

本目錄採用**碎形設計 (Fractal Design)**，個人與團隊都具備類似的工作管理目錄，實踐「由下而上 (Bottom-up)」的知識彙整：

- **`workmgr/`**：團隊級別的大腦，負責放置 Roadmap、團隊 Task 與統整後的團隊對合小報。
  - `inbox/`：接收來自成員個人提報的「對合包」。
  - `outbox/`：團隊對所有成員的「全局廣播庫」。
- **`members/`**：個人單元的私有實驗室 (PA Sandbox)。
  - 每位成員在自己的 `workmgr/` 中管理本地資訊，當確認完成且裁決後，才將檔案推送到 `sync/outbox/` 與團隊進行對合。

👉 詳細請見：[架構設計說明 (docs/architecture.md)](docs/architecture.md)

## ⚖️ 運作守則

在虛擬企業中，我們「不靠默契，靠協議」！
- **團隊憲法：** [團隊運作說明書 (TEAM_HANDBOOK.md)](rules/TEAM_HANDBOOK.md)
- **溝通格律：** [團隊工具使用與對齊指引 (TEAM_TOOLS_GUIDE.md)](rules/TEAM_TOOLS_GUIDE.md)

## 🚀 快速開始

1. 新成員加入時，請複製 `members/_template/` 目錄，並重新命名為你的帳號（例如：`members/wuulong/`）。
2. 在自己的 `workmgr/` 中進行日常任務操作。
3. 遵循 [規則指南](rules/) 發布與接收對合請求。

> ⚠️ 本 repo 為企業級 AI 轉型實驗基礎設施，請嚴格遵守工具指引以利未來 SyncHub (團隊 AI) 的自動化介入。
