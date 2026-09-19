# 人脈名片 (little-days-cards)

手機優先、關係導向的 PWA 名片管理工具。

## v0.3.0

這一版把產品重心從「填名片表單」改成「最低成本收進來，之後找得到、記得住、追得上」。

### 快速收進來
- 掃描名片與照片保存
- 裝置端 OCR（繁中 + 英文）與欄位自動對應
- 快速新增：首頁只要求姓名、公司、手機、Email
- 其他欄位預設收在「更多資料」
- 語音補備註
- 重複人脈偵測與合併
- vCard (.vcf) 匯入

### 人脈與跟進
- 姓名、公司、職稱、專案、場合、標籤、備註、互動紀錄全文搜尋
- 最愛／待追蹤／最近新增篩選
- 每位聯絡人的互動時間軸
- 下次追蹤日期
- 產生行事曆事件 (.ics)
- 電話、Email、Apple Maps 快捷操作

### 我的數位名片
- 個人數位名片
- 裝置端 QR Code
- vCard 一鍵分享
- Apple Wallet 介面預留（正式 .pkpass 仍需 Apple 憑證與簽章後端）

### 資料安全
- IndexedDB 本機資料庫
- JSON 完整備份／恢復
- iPhone 分享表可直接把備份存到「檔案 / iCloud Drive」
- CSV 匯出
- PWA 離線快取
- 更新版本不清空既有 IndexedDB 資料

## 部署

GitHub Pages 使用 GitHub Actions 自動部署 main branch。
