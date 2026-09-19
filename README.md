# 人脈名片 (little-days-cards)

手機優先、關係導向的人脈管理 PWA。

## v0.6.0 — Free-first AI Assistant

這一版把 AI 使用方式改成「免費優先」。預設不呼叫 OpenAI API，也不會因為打開 AI 助理而產生額外 API 費用。

### 已完成

#### AI 人脈助理
- 首頁主入口改成「AI 人脈助理」
- 預設為「免費模式」
- 可加入：
  - 名片照片
  - PDF
  - Excel / CSV
  - vCard
  - JSON
  - 文字檔
- 可補充情境，例如：
  - 這些都是今天台中港會議認識的
  - 全部標記新北、交通工程
- App 會自動產生 Little Days 專用的 ChatGPT 整理指令
- 支援 iPhone 分享表，把附件與整理指令一起交給 ChatGPT
- 若分享附件不支援，會改成複製整理指令供手動貼到 ChatGPT

#### ChatGPT 結果回填
- 可直接貼上 ChatGPT 回傳的 JSON
- 也可選擇 ChatGPT 產生的 JSON 檔
- 單一人物：
  - 直接回填姓名、公司、部門、職稱、手機、公司電話、Email、地址、網站、場合、專案、備註與標籤
  - 再由使用者確認後儲存
- 多位人物：
  - 自動送進匯入預覽
  - 去重
  - 標記需要確認的項目
  - 批次加入人脈資料庫
- 保留來源為 ChatGPT
- 保留 AI 信心資訊與 needsConfirmation

#### API 費用防呆
- 全自動 API 模式不是預設
- 點選 API 模式時會先出現明顯的費用警示視窗
- 明確說明 OpenAI API 與 ChatGPT 訂閱分開計費
- 必須主動勾選「我知道 API 可能另外收費」
- 未勾選時不能繼續
- 即使確認，目前也只會進入「尚未連線」頁面
- v0.6 不會偷偷呼叫任何付費 OpenAI API
- 真正建立後端與 API Key 前，仍不會產生 API 使用費

#### 原有功能保留
- 檔案匯入中心
- CSV / Excel / vCard / JSON 匯入
- 智慧欄位對應
- 重複資料偵測
- 匯入批次與整批復原
- 待整理名片
- 本機 OCR fallback
- 人脈搜尋
- 標籤 / 最愛 / 追蹤
- 互動紀錄
- 數位名片
- 完整 JSON 備份 / 恢復
- CSV 匯出

### 免費模式使用流程

1. 打開「AI 人脈助理」
2. 加入照片或檔案
3. 可補充認識場合 / 專案 / 標籤需求
4. 按「免費交給 ChatGPT 整理」
5. 在 iPhone 分享表選 ChatGPT
6. ChatGPT 依 Little Days 格式回傳 JSON
7. 回到 App，貼上 JSON 或選 JSON 檔
8. App 自動回填或進入批次匯入預覽

### 尚未完成

#### 全自動 OpenAI API
未來若使用者明確同意付費方案，才會再做：
- 安全 Serverless 後端
- OpenAI API Key 保護
- App 內直接送照片 / PDF / 表格到模型
- Structured Output
- 自動回填，不需手動來回 ChatGPT
- API 使用量 / 月預算 / 停用上限

目前沒有設定這些功能，因此 v0.6 的 AI 路徑預設是免費 ChatGPT Bridge。

#### 其他後續
- iPhone Share Extension
- 原生 iOS VisionKit
- 更完整重複人物合併介面
- PDF 多頁 / 多名片拆分
- 跨裝置雲端同步
- Apple Wallet .pkpass

## 部署

GitHub Pages 使用 GitHub Actions 自動部署 main branch。
