# 聯絡我們規格：contact.html

## 輸出位置與依循規格

- HTML 輸出：`WebPage_11515220/pages/contact.html`
- 共用設計依據：[site.md](site.md)；共用樣式與導覽互動位置同 site.md。
- 文件標題：`聯絡我們｜咒術回戰`；description：`咒術回戰主題介紹網站聯絡資訊，實際資料待補。`
- 文件語言 `zh-Hant`，viewport `width=device-width, initial-scale=1`。

## 區塊順序與詳細內容

1. **Skip link**：「跳至主要內容」，目的地 `#main`。
2. **共用 header/navigation**：品牌連到 `index.html`；導覽連到首頁、關於、聯絡；聯絡頁在 header 及 footer 都標 `aria-current="page"`。手機選單細節依 [site.md](site.md)。
3. **Page hero**：眉題 `SAY HELLO · SHARE YOUR STORY`；H1「聯絡我們」；簡介「歡迎與我們分享你對故事、角色與收藏的想法。」；背景為深色紅藍漸層與裝飾大字「参」。
4. **聯絡資訊 `.contact-section`**：白底桌面雙欄。
   - 左側眉題 `GET IN TOUCH`；標題「期待聽見你的咒術故事。」；說明「目前尚未提供實際營運聯絡資料，以下項目待網站負責人補充後更新。」；旁有 CSS 印章字「連絡」（裝飾）。
   - 右側四列，每列有圖示字、欄名、文字「待補」和狀態「待確認」：地址（地）、電話（話）、Email（信）、營業時間（時）。這些都是純文字，沒有 `tel:`、`mailto:`、Google Maps 或其他目的地。
5. **補充說明 `.contact-note`**：淡灰紫底；眉題 `A NOTE`；正文「補齊地址、電話、Email 與營業時間後，請再更新本頁；確認實際地址後再加入地圖連結。」；文字連結「先認識我們 →」到 `about.html`。
6. **共用 footer**：品牌、「讓 GOJO，陪你一起戰鬥。」、三頁導覽；本頁連結標目前頁面；版權列依 [site.md](site.md)。

## 排列與手機呈現

- Page hero 桌面 padding 88px 0 94px；≤480px padding 68px 0。右側大圓裝飾溢出裁切。
- 聯絡區桌面 `.8fr 1.2fr`、gap 80px；聯絡列以 42px 圖示欄、內容欄、狀態欄構成，垂直 padding 19px，列間有底線。
- ≤780px 改單欄、gap 26px，左側 intro 與資訊列表上下排列。
- ≤480px 聯絡列改兩欄（42px 圖示＋內容），「待確認」移至第二欄下一行；標題、正文自然換行。
- 聯絡補充區 desktop padding 38px；全站 section/mobile 規則見 [site.md](site.md)。

## 互動、連結及未完成項目

- 「先認識我們」只連到 `about.html`；沒有聯絡表單、提交按鈕、外部地圖、撥號、寄信或 API。
- 地址、電話、Email、營業時間四欄均待網站負責人提供。取得有效資料後才可依 sitemap 加入相應連結。
- Header/footer 導覽選單依 [site.md](site.md) 的共用 JavaScript 操作；其他區塊沒有額外 JavaScript。
