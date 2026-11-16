1. 專案目的 (Project Overview)
本專案是一個純靜態的「美食介紹與食記分享網站」，旨在以清晰、統一的版面記錄各類餐廳特色、必點菜色、價位與用餐心得。 本規範的設計目標是讓 AI 助手在未來新增餐廳介紹頁面時，無需人工重新解釋排版，即可快速產出視覺與結構完全一致的新頁面，並自動更新首頁索引。

2. 技術棧與檔案結構 (Tech Stack & Directory Structure)
技術限制：僅使用純靜態 HTML5、CSS3 與原生 JavaScript（Vanilla JS），嚴禁引入 React、Vue、Tailwind CSS 或任何需要編譯打包的外部框架，確保可直接部署於 GitHub Pages。
目錄結構：
/
├── AGENTS.md           # 本專案開發規範文件
├── index.html          # 網站首頁（包含分類篩選與所有美食卡片列表）
├── assets/
│   ├── css/
│   │   └── style.css   # 全站共用樣式表（所有頁面必須引入此檔案）
│   └── images/         # 存放食物與店面照片（若無實體圖片，可使用佔位圖或 CSS 色塊）
└── reviews/            # 存放所有獨立的美食介紹子頁面
    └── [slug].html     # 單一餐廳介紹頁（檔名一律全小寫英文與連字號，如 beef-noodles.html）
視覺與設計風格 (Design & Styling Rules) 整體氛圍：溫暖、有食慾、乾淨易讀的現代美食部落格風格。
配色系統（CSS 變數定義於 style.css）：

背景主色：#FAF8F5（暖米白）

卡片底色：#FFFFFF（純白，搭配微弱陰影 0 4px 12px rgba(0,0,0,0.06)）

主強調色：#D9534F（暖磚紅，用於標籤、按鈕、重點價格）

次強調色：#F0AD4E（暖橘黃，用於星等評分 ★）

主要文字：#2C2C2C（深炭灰），次要文字：#666666

字體與排版：

使用系統無襯線字體（Noto Sans TC, Microsoft JhengHei, sans-serif）。

內容區塊最大寬度限制為 900px 並置中對齊，確保手機與桌面端皆有良好閱讀體驗（RWD）。

共用元件：所有頁面（包含 index.html 與 reviews/*.html）都必須包含相同的頂部導覽列（Navbar，含網站標題與「回首頁」連結）以及頁尾（Footer）。

頁面結構規範 (Page Templates) A. 首頁 (index.html) Hero 區塊：網站主標題、副標題與簡短介紹。
分類篩選列（選用 JS 互動）：可依「全部 / 正餐 / 甜點下午茶 / 小吃」篩選下方卡片。

美食卡片網格 (Card Grid)：每張卡片必須包含：

餐廳名稱與分類標籤（Tag）

推薦星等（1～5 顆星）與平均消費區間（如 $150 - $250）

一句話短評（不超過 40 字）

「閱讀完整食記」連結（連向 reviews/[slug].html）

B. 美食介紹子頁面 (reviews/[slug].html) 每個新增的美食頁面必須嚴格遵守以下從上到下的區塊順序：

導覽列 (Navbar)：包含「← 返回美食列表」連結（指向 ../index.html）。

標題與基本資訊卡 (Header & Meta Box)：

餐廳名稱（

）、分類標籤、推薦星等
資訊網格：地址、營業時間、平均價位、推薦指數

必點菜色推薦 (Must-Order Dishes)：使用條列或小卡片列出 2～3 道招牌菜色與簡短口感描述。

詳細用餐心得 (Review Content)：分為「環境氛圍」與「餐點口味」兩個小段落。

底部導覽：提供「上一間餐廳 / 下一間餐廳」或「返回首頁」按鈕。

新增內容標準作業流程 (Workflow for Adding New Content) 當使用者要求「新增一間餐廳介紹」或「新增一篇美食頁面」時，AI 必須依序執行以下 3 個步驟，缺一不可：
建立子頁面：在 reviews/ 資料夾下建立新的 HTML 檔案（如 reviews/matcha-cafe.html），完全套用上述「B. 美食介紹子頁面」結構，並正確引入 ../assets/css/style.css。

同步更新首頁：打開 index.html，在「美食卡片網格」的最前方插入這間新餐廳的對應卡片，確保首頁連結能正確連向剛建立的檔案。

檢查一致性：確認沒有修改到 style.css 的既有全域變數，且所有相對路徑（../index.html、../assets/...）皆正確無誤。
