# 人脈名片 (little-days-cards)

手機優先、關係導向的人脈管理 PWA。

## v0.5.0 — AI Import Center

這一版把 App 從「掃名片」再往前推成「把散落在不同 App、相簿與檔案裡的人脈一次收回來」。

### 已完成

#### AI 匯入中心
- 首頁主入口改成「AI 匯入中心」
- 名片照片可從相簿一次多選，直接送進待整理匣
- 支援匯入：
  - CSV
  - Excel (.xlsx / .xls)
  - vCard (.vcf)
  - JSON
  - 圖片
- PDF 可被辨識為待處理來源，但真正拆解內容仍等待 ChatGPT Vision 後端
- 自動偵測來源 App / 檔名並保留來源資訊
- 智慧欄位對應：例如 Full Name → 姓名、Organization → 公司、Tel Work → 公司電話
- 匯入前預覽：
  - 偵測總數
  - 可直接匯入
  - 疑似重複
  - 需要確認
- 可用資料才會被批次加入，疑似重複與缺姓名資料暫不自動寫入

#### 自動分類
- 保留「原始匯入資料」與「衍生分類」分層
- 本機智慧規則可初步分類：
  - 公部門
  - 工程顧問
  - 建設／開發
  - 學術研究
  - 金融
  - 一般企業
- 專業領域可初步標示：
  - 交通運輸
  - 道路
  - 停車
  - 自行車
  - 都市規劃
  - 軌道運輸
- 衍生分類可被全文搜尋，但不覆蓋原始資料

#### 去重與匯入批次
- Email 優先比對
- 手機號碼比對
- 姓名＋公司比對
- 同一匯入檔內重複偵測
- 每次正式匯入都建立 Batch
- 最近匯入可查看
- 可「復原」某次匯入，刪除該批次新建立的人脈

#### Capture Inbox
- 拍照後先保存，不必等待 OCR
- 連續掃描
- 相簿多張匯入
- App 開著時依序處理
- 中途離開後資料仍保留，下次開啟續跑
- 本機 OCR 暫時保留作為 fallback

#### 備份與資料安全
- 完整 JSON 備份包含：
  - 人脈資料
  - 名片照片
  - 互動紀錄
  - 待整理名片
  - 我的數位名片
  - App 設定
  - 匯入批次歷史
- schema version
- 合併恢復
- 整份取代
- 整份取代前先建立「恢復前備份」
- iPhone 分享表可存到 iCloud Drive / Google Drive
- CSV 匯出
- App 更新不清空 IndexedDB

### 尚未完成

#### ChatGPT / OpenAI Vision
目前還沒有把 OpenAI API key 暴露在前端。真正的下一階段是：

照片 / PDF
→ 安全後端
→ OpenAI Vision
→ Structured Output
→ 名稱、公司、部門、職稱、手機、公司電話、Email、地址、網站
→ 信心值
→ 回填 AI Inbox 草稿

這需要 Serverless 後端（例如 Cloudflare Worker / Vercel Function / Supabase Edge Function）保護 API key。

#### AI 級欄位理解與分類
目前 CSV / Excel 的欄位對應與分類是本機智慧規則，不是 LLM。接上 OpenAI 後再升級為：
- 任意欄名理解
- PDF / 圖片內容理解
- 更好的公司類型與專業領域分類
- 自動標籤
- 自動判斷疑似同一人物
- 低信心欄位只要求使用者確認

#### 其他後續
- iPhone Share Extension：直接從「照片 / 檔案」分享進 App
- 真正跨裝置雲端同步
- 原生 iOS 文件掃描 / VisionKit
- Apple Wallet .pkpass
- 更完整的重複資料合併介面
- PDF 多頁／多名片智慧拆分

## 部署

GitHub Pages 使用 GitHub Actions 自動部署 main branch。
