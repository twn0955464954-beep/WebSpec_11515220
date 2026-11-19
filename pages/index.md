# 首頁規格：index.html

## 輸出位置與依循規格

- HTML 輸出：`WebPage_11515220/pages/index.html`
- 共用設計依據：[site.md](site.md)；樣式 `WebPage_11515220/pages/assets/css/site.css`，互動 `WebPage_11515220/pages/assets/js/site.js`。
- 文件標題：`首頁｜咒術回戰`；description：`咒術回戰主題介紹網站，認識咒術世界的角色、理念與交流方式。`
- 文件語言 `zh-Hant`，viewport 為 `width=device-width, initial-scale=1`。

## 區塊順序與詳細內容

1. **Skip link**：文字「跳至主要內容」，目的地 `#main`，鍵盤 focus 時可見。
2. **共用 header/navigation**：品牌圖章「呪」、品牌名「咒術回戰」、英文副標 `JUJUTSU KAISEN`；品牌連到 `index.html`。導覽順序首頁、關於我們、聯絡我們；首頁連結在 header 及 footer 都設 `aria-current="page"`。手機操作細節見 [site.md](site.md)。
3. **Hero 主視覺**：深墨紫底，桌面文案／圖片雙欄，文字欄先、圖像欄後。眉題 `CURSED ENERGY · UNBREAKABLE WILL`；H1「一拳黑閃，灌爆你。」在「黑閃，」後換行；副文案「請加入我們的戰鬥吧。走進咒術的世界，認識那些在危機中仍選擇守護他人的身影。」；輔助文字 `COURAGE IS A CHOICE · 勇氣，始於選擇`。
   - 圖片：`assets/images/yuji.jfif`；替代文字「咒術回戰角色虎杖悠仁主題插畫」。CSS 環、斜線、右下 `ENERGY / 01` 為裝飾，標 `aria-hidden`。
   - 按鈕「認識我們 ↗」到 `about.html`；「聯絡我們」到 `contact.html`。
   - Hero 下緣「向下探索 ↓」連到本頁 `#intro`。
4. **品牌簡介 `#intro`**：白底雙欄；左側眉題 `A WORLD OF CURSES`、標題「直面恐懼，仍然向前。」（換行）；右側正文：「咒術回戰以咒力與咒靈交織出緊張的冒險，也描寫人在困境裡的選擇、羈絆與成長。這裡以主題介紹的方式，邀你從角色與故事出發，感受那份不服輸的力量。」下方連結「閱讀品牌故事 →」到 `about.html`。
5. **特色卡片 `.features`**：紙白底；眉題 `WHAT WE CELEBRATE`、標題「把熱愛，化成日常收藏。」、說明「從閱讀到收藏，為每一份喜愛留一個位置。」下方桌面三欄卡片，手機單欄：
   - `01 / READ`，符號「冊」，標題「精選漫畫書」，正文「以漫畫閱讀故事脈絡，重新感受每場戰鬥與角色成長。」
   - `02 / COLLECT`，符號「像」，標題「角色公仔」，正文「讓喜愛的角色化作桌邊風景，收藏每一份熱血記憶。」
   - `03 / CONNECT`，符號「結」，標題「同好交流」，正文「帶著你的喜愛與想法，和更多咒術粉絲分享故事。」
   卡片不是連結，也沒有 JS 點擊功能。
6. **結尾 CTA `.closing`**：深墨底、置中文字；眉題 `READY TO JOIN?`、標題「下一場冒險，等你一起。」、說明「想了解更多？歡迎前往關於頁，或與我們聯絡。」按鈕「前往聯絡我們 ↗」到 `contact.html`。
7. **共用 footer**：品牌、slogan「讓 GOJO，陪你一起戰鬥。」及頁尾三頁連結；首頁連結標目前頁面。版權列如 [site.md](site.md)。

## 排列與手機呈現

- 桌面 hero min-height 640px，`.hero-grid` 兩欄各 1fr，gap 30px，圖片舞台 420px 高；h1 46–76px clamp。
- ≤780px hero 改單欄文字布局，圖片舞台絕對定位在右側、390×390px、opacity `.56`；文字置前，遮罩加深。主標最大寬約 540px。
- ≤480px hero 內容上下 padding 62px/68px；h1 43–58px clamp；圖片舞台右移至 `right:-160px`、`top:120px` 並降至 opacity `.38`，作背景裝飾；按鈕 gap 9px、水平 padding 17px。
- intro 桌面 `.85fr 1.15fr`、gap 90px；中小尺寸單欄，≤780px gap 10px。
- 特色卡桌面三欄，≤780px 單欄；≤780px 卡片不保留 250px 固定最小高。
- CTA 桌面 padding 82px；≤480px 70px。

## 互動、連結及未完成項目

- 只有導覽選單有 JavaScript 互動，依 [site.md](site.md) 規則運作。
- 其餘按鈕／文字連結為標準 HTML 錨點，沒有 AJAX 或表單。
- 唯一 raster 圖片是本地虎杖圖；若替換圖片，需同步改 `src` 並保留描述性 alt。主視覺周圍的紅藍環、光暈與 slash 是 CSS，不是獨立素材。
- 本頁簡介及卡片介紹為示範文案，品牌正式介紹尚待確認。
