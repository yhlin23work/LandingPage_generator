# 🛠 Landing Page 產生器

CMoney 產品 Landing Page 快速生成工具。填寫表單 → 即時預覽 → 一鍵下載完整打包檔。

---

## 快速開始

用瀏覽器（建議 Live Server）開啟 `index.html` 即可使用，無需安裝任何套件。

```
LandingPage_generator/
├── index.html        ← 產生器主程式（直接開啟）
├── spec.html         ← 詳細網頁規格書
├── README.md         ← 本文件
└── assets/
    └── images/
        ├── SharedImages/             ← 共用圖片（每次打包自動納入）
        │   ├── appstore-badge.png
        │   ├── appstore-badge@2x.png
        │   ├── play-badge.png
        │   ├── play-badge@2x.png
        │   ├── cellphone_downloadCTA.png
        │   └── event-tracking-guide.png  ← 事件埋點位置示意圖（小工具用）
        ├── theme pic.jpg
        ├── qrcode.png
        └── features/
            ├── feat1.png ～ feat6.png
```

---

## 介面說明

介面分為左右兩欄：

| 區塊 | 說明 |
|---|---|
| 左欄（工具面板） | 填寫產品資訊的表單區 |
| 右欄（預覽區） | 即時預覽產生的 Landing Page |

頂部列右側可切換 **桌機 / 手機** 預覽模式。

---

## 表單欄位說明

### 1. Header
| 欄位 | 說明 |
|---|---|
| 產品名稱 | 顯示於 Header、Hero、頁尾，也用於下載檔名 |
| 品牌副標題 | Header 品牌名下方的一行說明文字 |
| App Icon 圖片 URL | Header / 頁尾的品牌小圖示 |

### 2. Hero 主視覺
| 欄位 | 說明 |
|---|---|
| Hero 主標題 | 頁面最大標題，留空沿用產品名稱 |
| Hero 介紹文字 | 主標題下方的說明段落 |
| 主要下載連結（CTA URL） | 「立即免費下載」按鈕的連結目標 |
| Hero 圖片 URL | 主視覺右側大圖（建議寬 560px 以上）|

### 3. Why 亮點區塊
最多 **2** 個亮點，每項包含 Icon（Emoji）、標題、強調資訊（大字數據）、說明文字。

### 4. 核心功能
最多 **6** 個功能卡片，每項包含標題、說明、截圖圖片。
- **桌機**：左側列表點選，右側顯示對應截圖
- **手機**：左右滑動的 Slider

### 5. 下載 CTA
| 欄位 | 說明 |
|---|---|
| 小標 | 下載區塊上方的小段文字（如 ⚡ 現在就加入 ⚡）|
| 主標題 | 下載區塊 H2，留空自動帶入「立即下載[產品名稱] 掌握先機」|
| 副標文字 | 主標題下方說明（可留白）|
| 下載連結（URL） | App Store / Google Play 的統一跳轉連結 |
| App Store 徽章 | 預設使用內建圖片，可自訂上傳 |
| Google Play 徽章 | 預設使用內建圖片，可自訂上傳 |
| QR Code 圖片 | 桌機點擊「免費下載」時彈出的 QR Code（可自動產生）|

### 6. （預留）

### 7. Footer
公司名稱、聯絡地址、版權年份。

---

## 分頁說明

表單分為三個分頁：**內容 / 顏色 / SEO與追蹤**

### 顏色分頁
| 欄位 | 說明 |
|---|---|
| 主色（Primary） | Header、標題、按鈕的主要色調 |
| 輔色（Secondary） | 下載按鈕、CTA 強調元素的強調色 |

> 背景色無須手動設定，會自動從主色與輔色推算出符合的淺色背景。

### SEO 與追蹤分頁
> ℹ️ 此分頁所有設定僅寫入網頁 `<head>`，**不會顯示於頁面上**。

| 欄位 | 說明 | 預設值 |
|---|---|---|
| 頁面 `<title>` | 瀏覽器分頁標題、Google 搜尋藍色標題 | 產品名稱｜品牌副標題 |
| Meta description | Google 搜尋結果摘要（建議 100–160 字） | Hero 介紹文字 |
| GA4 Measurement ID | 填入後自動注入 `gtag.js`，格式 `G-XXXXXXXXXX` | 留空不注入 |
| Meta Pixel ID | 填入後自動注入 `fbevents.js`，填入純數字 ID | 留空不注入 |

**事件埋點對應規則**（點擊「位置示意圖」可查看標記截圖）：

| 按鈕類型 | 數量 | GA4 事件 | Meta 事件 |
|---|---|---|---|
| 🟢 下載按鈕（Header 免費下載、Hero 立即免費下載、App Store badge、Google Play badge）| 4 | `click_app_download` | `Lead` |
| 🔴 互動按鈕（Header 特色功能、Hero 看功能介紹 等）| 8 | `click_cta` | `ClickCTA` |

---

## 小工具 UI 介面

```
┌──────────────────────────────────────────────────────────────────┐
│  🛠 Landing Page 產生器  [🗑清空] [範例] [⬆匯入]   預覽  🖥  📱  │  ← 頂部列
├───────────────────────────┬──────────────────────────────────────┤
│  [ 內容 | 顏色 | SEO與追蹤 ]│                                      │
│  ┌── 1 Header ──────────┐ │                                      │
│  │ 產品名稱             │ │                                      │
│  │ 品牌副標題           │ │       Landing Page 預覽區            │
│  │ App Icon 圖片        │ │       （iframe）                     │
│  └──────────────────────┘ │                                      │
│  ┌── 2 Hero 主視覺 ─────┐ │                                      │
│  └──────────────────────┘ │                                      │
│  ┌── 3 Why 選擇我們 ────┐ │                                      │
│  └──────────────────────┘ │                                      │
│  ┌── 4 核心功能 ────────┐ │                                      │
│  └──────────────────────┘ │                                      │
│  ┌── 5 下載 CTA ────────┐ │                                      │
│  └──────────────────────┘ │                                      │
│  ┌── 7 Footer ──────────┐ │                                      │
│  └──────────────────────┘ │                                      │
│ ─────────────────────────│                                      │
│  [🗑清空] [▶預覽] [⬇下載打包]                                    │  ← action bar
└───────────────────────────┴──────────────────────────────────────┘
      左欄 480px（工具面板）              右欄 1fr（預覽區）
```

| UI 元件 | 說明 |
|---|---|
| 頂部列左欄 | 工具標題 ＋ 清空設定 / 載入範例 / 匯入 ZIP 按鈕，深藍底色 |
| 頂部列右欄 | 「預覽畫面」標籤 ＋ 桌機／手機切換按鈕，深灰底色 |
| 表單分頁 | 內容 / 顏色 / SEO與追蹤，三個分頁切換 |
| 內容分頁 | 7 個可折疊 Accordion 區塊，可捲動 |
| 預覽面板 | Blob URL iframe，桌機模式 100% 寬 / 手機模式 375px 置中 |
| Action Bar | 固定於表單底部，「🗑 清空設定」＋「▶ 預覽頁面」＋「⬇ 下載打包」 |
| 側欄收合鈕 | 頂部列左上角，可收合工具面板以全螢幕預覽 |
| 視窗 ≤ 959px | 預覽區自動隱藏，僅顯示工具面板 |

---

## 下載按鈕行為

| 裝置 | 行為 |
|---|---|
| 桌機 | 彈出 QR Code Modal，讓使用者用手機掃描下載 |
| 手機 | 捲動至下方下載區塊（含 App Store / Google Play 連結）|

> 在小工具預覽時，行為依頂部列的「桌機 / 手機」切換按鈕判斷，不受視窗寬度影響。

---

## 載入範例 / 匯入 ZIP

| 功能 | 說明 |
|---|---|
| **範例**（頂部列）| 載入 `LandingPage_chipk/` 資料夾中的範例頁面，自動填入所有欄位 |
| **⬆ 匯入**（頂部列）| 選取先前下載的 `.zip` 檔，自動解析並回填所有欄位（含 GA4/Pixel ID）|

> 匯入 ZIP 時會自動讀取：內容欄位、顏色、圖片、SEO 設定、GA4 Measurement ID、Meta Pixel ID。

---

## 下載打包

點擊「⬇ 下載打包」會產生 ZIP 檔，結構如下：

```
LandingPage_[產品名稱].zip
└── LandingPage_[產品名稱]/
    ├── index.html          ← Landing Page 主檔
    ├── styles.css          ← 樣式表
    └── assets/
        └── images/
            ├── assets/images/SharedImages/appstore-badge.png        ┐
            ├── assets/images/SharedImages/appstore-badge@2x.png     │ 共用圖片（自動納入）
            ├── assets/images/SharedImages/play-badge.png            │
            ├── assets/images/SharedImages/play-badge@2x.png         │
            ├── assets/images/SharedImages/cellphone_downloadCTA.png ┘
            ├── qrcode.png        ← 若表單有填入本地路徑
            ├── theme pic.jpg     ← 若表單有填入本地路徑
            └── features/         ← 若表單有填入本地路徑
                └── feat1.png ...
```

**共用圖片**（`SHARED_ASSETS`）每次打包都自動納入，不需手動設定：
- `appstore-badge.png` / `appstore-badge@2x.png`
- `play-badge.png` / `play-badge@2x.png`
- `cellphone_downloadCTA.png`

> 外部 URL 圖片（https://...）不納入打包，保留原始連結。

---

## 注意事項

- 圖片透過「上傳」方式加入，下載打包時會自動以正確路徑嵌入 ZIP
- 下載的 ZIP 解壓後，直接用瀏覽器開啟 `index.html` 即可查看完整 Landing Page
- GA4 / Meta Pixel 追蹤碼只會寫入下載後的 Landing Page，小工具本身不會送出任何追蹤事件
- `event-tracking-guide.png` 僅供小工具的說明 Modal 使用，不會被納入 ZIP 打包
- 詳細技術規格請參閱 [spec.html](spec.html)
