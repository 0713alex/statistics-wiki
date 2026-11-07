# Statistics Wiki

現代 Dashboard 風格的統計學知識庫，包含統計推論、迴歸分析、存活分析、模型評估四個分類。使用 Markdown + `data/articles.json` 管理文章，AI 擴充規範請見 [AGENTS.md](AGENTS.md)。

## Local preview

因為網站透過 `fetch()` 載入 Markdown，請使用本機 HTTP 伺服器，不要直接雙擊 `index.html`：

```bash
python -m http.server 8000
```

瀏覽 `http://localhost:8000/`。

## GitHub Pages deployment

1. 在 GitHub 建立公開儲存庫 `statistics-wiki`。
2. 將本資料夾的**內容**推送至儲存庫根目錄（確保 `index.html` 位於根目錄）。
3. 進入 **Settings → Pages → Build and deployment**，選擇 **Deploy from a branch**、`main`、`/(root)`，儲存。
4. 部署完成後開啟 `https://USERNAME.github.io/statistics-wiki/`（將 USERNAME 替換成 GitHub 帳號）。

## How to add content

先閱讀 `AGENTS.md` 和 `templates/article-template.md`。在 `content/<category>/` 新增文章，並將對應資料加入 `data/articles.json`。側邊分類與文章列表由索引自動生成，不需新增 HTML 頁面。

## Notes

網頁使用 CDN 載入 marked、DOMPurify、MathJax，首次開啟需連網。示例內容用於教學，不是研究資料或實際 SAS/R 執行結果。
