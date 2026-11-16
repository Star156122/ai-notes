# CLAUDE.md — AI 小筆記（ai-notes）

> AI 讀完這份文件後，應該能在不詢問使用者的情況下，依相同規則新增或修改頁面。

## 1. 專案目的
- 這是一個個人學習筆記網站，主題是「AI 工具與 Vibe Coding 入門」。
- 目標讀者：剛接觸 AI 工具的同學。語氣：親切、簡潔、繁體中文（台灣用語）。
- 每篇筆記獨立成一頁，首頁負責列出所有筆記。
- 網站以 GitHub Pages 發布，**純靜態**：只用 HTML + CSS，不使用框架、不需要建置步驟、不引入外部 JS 套件。

## 2. 目錄結構
```
/
├── CLAUDE.md              # 本文件（專案規則）
├── README.md              # 給人看的簡介
├── index.html             # 首頁：筆記卡片列表
├── assets/
│   └── style.css          # 全站唯一樣式檔
├── notes/
│   └── NNN-slug.html      # 每篇筆記，例如 001-what-is-claude-md.html
└── templates/
    └── note-template.html # 新增筆記時複製這份
```

## 3. 新增筆記的標準流程（AI 必須照順序做）
1. 複製 `templates/note-template.html` 到 `notes/NNN-slug.html`。
2. 編號 `NNN` 為三位數流水號，接在現有最大編號之後（先檢查 `notes/` 目錄）。
3. `slug` 使用小寫英文與連字號，例如 `prompt-basics`；不可使用中文或空白。
4. 填入內容，保留模板的所有區塊與 class 名稱。
5. 到 `index.html` 的 `<!-- NOTES-LIST -->` 區塊，**在最前面**加入一張新卡片（新到舊排序）。
6. 檢查：所有連結皆為相對路徑、頁面可離線開啟、無壞連結。

## 4. 筆記頁面格式
- `<title>` 格式：`筆記標題｜AI 小筆記`
- 頁面固定包含：
  1. `<header class="site-header">`：返回首頁連結 `../index.html`
  2. `<h1>` 標題 + `<p class="meta">`（日期 `YYYY-MM-DD`、標籤）
  3. `<section class="summary">`：3 行內的重點摘要
  4. 內文：用 `<h2>` 分段，每段不超過 5 句；程式碼用 `<pre><code>`
  5. `<section class="takeaway">`：我的心得／下一步
  6. `<footer>`：上一篇／下一篇連結（沒有則省略）
- 每篇長度約 300–800 字。一個 `<h1>`，標題層級不可跳級。
- 圖片放 `assets/img/`，一定要有 `alt` 文字。

## 5. 首頁卡片格式
```html
<a class="card" href="notes/NNN-slug.html">
  <span class="tag">標籤</span>
  <h2>筆記標題</h2>
  <p>一句話簡介（40 字內）</p>
  <time datetime="YYYY-MM-DD">YYYY-MM-DD</time>
</a>
```

## 6. 視覺風格
- 簡約、留白多、閱讀優先。淺色背景、深灰文字。
- 色彩只能使用 `assets/style.css` 中 `:root` 的 CSS 變數（`--bg`、`--text`、`--accent`…）。
- 字體使用系統字體堆疊，內文行高 1.8，內容寬度上限 720px。
- 必須支援手機版（RWD）；不得在頁面內寫行內樣式（`style="..."`），要改外觀就改 `style.css`。
- 新增元件時，先在 `style.css` 加 class，再使用。

## 7. AI 的行為規則
**必須：**
- 先讀 `CLAUDE.md` 與現有 `notes/` 再動手，風格需與既有頁面一致。
- 只修改任務需要的檔案；改動後簡短說明改了什麼。
- 內容不確定時寫明「待查證」，不可捏造事實、數據或引用。

**禁止：**
- 引入框架、CDN 套件、追蹤碼或廣告。
- 刪除或改名既有筆記（會破壞連結）。
- 貼上大段他人著作原文；引用請改寫並附來源連結。
- 修改本文件，除非使用者明確要求。

## 8. 完成檢查清單
- [ ] 檔名符合 `NNN-slug.html`
- [ ] 首頁已加入卡片
- [ ] 標題、日期、摘要、心得區塊齊全
- [ ] 無行內樣式、無壞連結
- [ ] 手機寬度（375px）下閱讀正常

## 9. 發布方式
- Push 到 `main` 分支，GitHub Pages 設定：Settings → Pages → Deploy from a branch → `main` / `(root)`。
- 網址格式：`https://<帳號>.github.io/<repo 名稱>/`
