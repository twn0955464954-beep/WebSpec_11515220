# 咒術回戰網站共用規格（依實作整理）

本文件記錄 `WebPage_11515220/pages/` 目前 HTML、CSS、JavaScript 的實際狀態，作為後續修改依據。這是實作盤點，不代表未完成內容已確認。

## 網站與檔案索引

| 用途 | 實際檔案 | 對應規格 |
|---|---|---|
| 首頁 | `WebPage_11515220/pages/index.html` | [index.md](index.md) |
| 關於我們 | `WebPage_11515220/pages/about.html` | [about.md](about.md) |
| 聯絡我們 | `WebPage_11515220/pages/contact.html` | [contact.md](contact.md) |
| 共用樣式 | `WebPage_11515220/pages/assets/css/site.css` | 本文件 |
| 共用導覽互動 | `WebPage_11515220/pages/assets/js/site.js` | 本文件 |
| 首頁主視覺 | `WebPage_11515220/pages/assets/images/yuji.jfif` | [index.md](index.md) |

HTML 位於同一層，以 `assets/...` 相對路徑載入素材、樣式與腳本。三頁皆為繁體中文文件（`lang="zh-Hant"`），有 viewport、description、各自的 title、skip link、header/nav/main/footer 等語意結構。JavaScript 使用 `defer` 載入。

## 共用視覺系統

### 色彩

CSS 自訂屬性定義於 `:root`。另有直接寫在元件上的輔助色，表中一併列出供延伸設計使用。

| 名稱 | 色碼／值 | 實際用途 |
|---|---|---|
| `--ink` | `#181722` | 主要深墨色、收尾 CTA 背景 |
| `--ink-soft` | `#282633` | 預留深色變數，目前未直接套用 |
| `--paper` | `#f7f5f4` | 頁面底色、特色區底色 |
| `--white` | `#fff` | 預留白色變數 |
| `--red` | `#d8263e` | 主紅、品牌標記、主要按鈕 |
| `--red-dark` | `#a8142b` | 紅色文字連結與 hover |
| `--red-pale` | `#ffe8eb` | 淺紅圖示底 |
| `--blue` | `#1878bd` | 藍色咒力點綴 |
| `--blue-pale` | `#e5f4ff` | 淺藍圖示底 |
| `--violet` | `#593b77` | 紫色特色圖示 |
| `--muted` | `#716d78` | 次要正文 |
| `--line` | `#e4dfe1` | 卡片邊框與分隔線 |
| `--shadow` | `0 20px 55px rgba(25,20,35,.12)` | 共用陰影值；卡片另有較淡陰影 |
| 輔助紅 | `#ff6377`, `#ff6579`, `#ff7586`, `#ff4059`, `#e2374f`, `#ef3b52`, `#ff4c62`, `#79182e` | 導覽 active/hover、眉題、標題、環形裝飾、環境示意圖 |
| 輔助藍 | `#57b6f5`, `#5aade9`, `#43a4e5`, `#227cb7`, `#173752` | 鍵盤 focus、環形裝飾、環境示意圖 |
| 輔助紫／灰 | `#302641`, `#1b1a27`, `#11121b`, `#191822`, `#262133`, `#1b3140`, `#171721`, `#242033`, `#f0edf0`, `#fff4f5`, `#7a4650`, `#eee8f5`, `#77717d`, `#f1eff2`, `#e9adb5`, `#c5c1cb`, `#c7c1cb`, `#b9b5c0`, `#aaa6b2`, `#aaa5b0`, `#99949f`, `#e8e4eb`, `#f4eff1`, `#393640`, `#46424e`, `#625e6b` | 漸層背景、卡片與狀態底色、次要文字、邊框 |
| 白／黑 | `#fff`, `#fff`、`rgba(255,255,255,...)`、`rgba(0,0,0,.25)` | 文字、底色、半透明層與陰影 |

另有多處 rgba 疊色：深色遮罩、紅藍光暈、邊框與陰影。主視覺不是單一純色，而是深墨紫底搭配紅藍放射漸層、環形線條和圖片。

### 字體與文字

- 中文／介面字體堆疊：`"Noto Sans TC", "Microsoft JhengHei", sans-serif`。HTML 沒有載入網路字體；若裝置沒有 Noto Sans TC，會依序使用微軟正黑體或系統 sans-serif。
- 標題 serif 堆疊：`"Noto Serif TC", "PMingLiU", serif`。HTML 未載入 Noto Serif TC 網路字體，顯示依裝置已安裝字型回退。
- body 基準：`16px / 1.8`（計算行高 `28.8px`），一般字重 400。
- `h1`、`h2`、`h3` 行高 `1.3`；`h1`、`h2` 使用 serif 並設 `font-weight:900`、`letter-spacing:.04em`。
- 常用尺寸：導覽 14px/700；eyebrow 11px/800、字距 `.2em`；按鈕 14px/800；卡片標題 20px；卡片正文 14px；頁尾導覽 13px；版權 11px；英文小標 9–10px。
- 響應式標題：首頁 hero h1 `clamp(46px,6.4vw,76px)`，手機 ≤480px 改 `clamp(43px,12vw,58px)`；一般 h2 `clamp(30px,4vw,46px)`，首頁 intro h2 `clamp(34px,4.4vw,52px)`；page hero h1 `clamp(42px,6vw,66px)`；聯絡 h2 `clamp(34px,4.5vw,52px)`。

### 版面、尺寸與間距

- 全域 `box-sizing:border-box`；body margin 0；段落與標題 margin-top 0。
- `.container` 桌面最大寬 `1120px`，寬度 `min(1120px, calc(100% - 48px))`，左右置中。
- ≤780px：容器寬度 `min(100% - 40px, 640px)`；≤480px：`calc(100% - 36px)`。
- header 桌面及中尺寸最小高度 78px；≤480px 最小高度 70px。
- 首頁 hero 桌面最小高度 640px；內容網格兩欄 `1fr 1fr`、間距 30px、上下 padding 82px。手機改單欄，hero grid 上下 padding 70px/78px；≤480px 改 62px/68px，藝術圖改絕對定位並裁切於右側。
- 共用 `.section` 桌面上下 padding 100px；≤480px 為 72px。
- about page hero 桌面 padding 88px 0 94px；≤480px 68px 0。
- 關於故事區兩欄、gap 78px；≤780px 單欄、gap 32px，故事圖排到文字後方。
- 聯絡區桌面兩欄 `.8fr 1.2fr`、gap 80px；≤780px 改單欄 gap 26px。
- 首頁特色卡桌面三欄、gap 18px；≤780px 單欄。理念卡桌面三欄、gap 16px；≤780px 單欄。
- 關於環境區桌面欄比例 `1.05fr .95fr`、gap 65px；≤780px 單欄。
- 全站主要斷點為 `780px` 與 `480px`。Reduced motion 媒體查詢停用平滑捲動並大幅縮短 transition/animation。

### 導覽列與頁尾

- 共用 header 為深色底 `rgba(24,23,34,.97)`、白字、底部半透明邊線；品牌標誌為紅底方形「呪」圖章（42×42px，≤480px 為 38×38px），品牌文字為「咒術回戰」，下方英文 `JUJUTSU KAISEN`。
- 品牌連結指向 `index.html`，有 `aria-label="咒術回戰首頁"`。導覽為「首頁」→`index.html`、「關於我們」→`about.html`、「聯絡我們」→`contact.html`。當頁在 header 與 footer 導覽各有一個連結標 `aria-current="page"`；桌面以紅色字與底線顯示，footer 以紅色字顯示。
- ≤780px 隱藏橫向導覽、顯示 44×44px 漢堡按鈕；選單由 JS 加上 `.is-open`，深色下拉，最大高 240px。≤480px header 70px，選單 top 改 69px（≤780px 是 77px）。
- 全頁前置 skip link「跳至主要內容」連到 `#main`，平常置於視窗上方，focus 時移至 top 12px。
- footer 深底 `#111018`、上方 padding 42px、底部 18px。桌面三欄：品牌、標語、頁尾連結；中尺寸兩欄並將導覽移至下一列；≤480px 單欄。版權列上方有細分隔線，文字為 `© 2026 咒術回戰主題介紹網站` 與 `本網站為主題介紹示範頁面`。
- 標語實際文字：「讓 GOJO，陪你一起戰鬥。」

### 按鈕、連結、卡片和圖像樣式

- `.button` 為 inline-flex，最小高 50px、水平 padding 23px、gap 12px、14px/800；hover 上移 3px。≤480px 水平 padding 17px。
- `.button-red` 紅底白字，hover 深紅；`.button-outline` 透明底、半透明白框白字，hover 白底深字；`.button-light` 白底深字，hover 紅底白字。
- `.text-link` 紅深色粗體、底線邊框、內含箭頭字元。它是普通錨點，不執行 JS。
- 首頁特色 `.feature-card` 白底、1px `--line` 邊框、padding 28px、min-height 250px、淡陰影；hover 上移 5px 並加深陰影。卡片內有序號、48×48px 色塊符號、標題與正文。≤780px 卡片單欄並取消固定最小高度。
- About 品牌堅持 `.value-item` 白底紅色 2px 上框、padding 24px；contact 聯絡列以水平分隔線和圖示色塊呈現。三者為不同內容元件，非單一共用卡片元件。
- 首頁使用實際 `<img>`：`assets/images/yuji.jfif`，alt 為「咒術回戰角色虎杖悠仁主題插畫」。其他視覺由 CSS 繪製，使用帶 `role="img"` 和 `aria-label` 的容器，不引用額外圖片檔。

## 共用互動與無障礙

### `assets/js/site.js`

- IIFE 啟動後尋找 `.menu-toggle` 與 `.site-nav`；其中任一不存在即結束，不執行其他操作。
- 點選 toggle：依 `aria-expanded` 反轉狀態，同步切換 nav `.is-open`，並更新 aria-label 為「開啟導覽選單」或「收合導覽選單」。
- 點選任一導覽連結會關閉選單並把 `aria-expanded` 設為 false。
- Escape 鍵會關閉選單，並將焦點移回 toggle。
- 視窗寬度大於 780px 時關閉選單。
- 沒有點擊選單外側關閉、沒有焦點陷阱、沒有路由/表單/API 功能；不要將這些記為已實作。

### 鍵盤與動態偏好

- `:focus-visible` 使用 3px `#57b6f5` 外框、offset 4px。
- skip link 支援鍵盤 focus 跳至 main。
- menu toggle 有 `aria-expanded`、`aria-controls="site-nav"` 與動態 aria-label；nav 有 `aria-label`。
- 裝置偏好 reduced motion 時關閉 smooth scroll、把動畫／轉場時間縮至 `.01ms`。
- 主要內容、header、nav、footer 使用語意元素；非必要裝飾環和箭頭多標為 `aria-hidden="true"`。

## 各頁規格入口

- [首頁詳細規格](index.md)：主視覺、品牌簡介、三項特色、CTA 及連結。
- [關於我們詳細規格](about.md)：品牌故事、三項堅持、空間示意與 CTA。
- [聯絡我們詳細規格](contact.md)：待補欄位、返回關於頁連結及未實作聯絡方式。

## 與原始 sitemap.md 的差異（供確認）

| sitemap 項目 | 實際網站狀態 | 待確認／說明 |
|---|---|---|
| 網站名稱及三頁架構 | 咒術回戰；首頁、關於、聯絡三頁一致 | 無差異 |
| 目標對象「喜歡咒術的各個角色」 | 實際文案稱「咒術粉絲／同好」 | sitemap 用詞「各個角色」可能原意是喜歡咒術的粉絲，請確認 |
| 首頁虎杖優人主題圖片 | 使用 `yuji.jfif`，alt 寫「虎杖悠仁」 | 圖片確實在規格提供資料夾；「優人／悠仁」文字有差異，實際替代文字採圖中角色常用姓名 |
| 首頁簡介只列「請加入我們的戰鬥吧」 | 保留該句，並補充咒術世界與守護者的示範介紹 | 延伸文案尚待確認 |
| 首頁三項特色列「精選漫畫書、公仔」 | 實際為漫畫書、角色公仔、同好交流 | 第三項為新增示範內容 |
| 關於頁成立起點 | 寫成「從喜愛故事與角色開始」；成立時間註明待提供 | 不是經核實的成立史，請提供正式資料 |
| 關於頁三項品牌堅持 | 尊重故事、用心挑選、真誠交流 | 依大綱撰寫的示範理念，尚待確認 |
| 環境介紹需圖片搭配文字 | 文字搭配 CSS 幾何空間示意，沒有實景照片 | 圖示不是實際店面照片；有場地照片可再替換 |
| 聯絡資料待補；有資料才加地圖/撥號/寄信 | 地址、電話、Email、營業時間均是待補；沒有外部聯絡連結或表單 | 符合 sitemap 規則；實際資料尚未完成 |
| 共用 slogan | 「讓 GOJO，陪你一起戰鬥。」 | 與最新 sitemap 一致 |
| 頁尾版權年 | 顯示 2026 | sitemap 未指定年度，請確認是否使用固定年份 |
