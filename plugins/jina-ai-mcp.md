# Jina AI MCP：網頁搜尋、閱讀與論文資料整理

查核日期：2026-11-02。依官方文件與當次 ChatGPT 連線提供的工具名稱整理；功能可能隨版本、客戶端設定與權限變動。

## 名稱速查

| 搜尋名稱／別稱 | 對應內容 |
| --- | --- |
| Jina AI MCP、Jina MCP、jina-ai-mcp | 這個工具整合的常見名稱 |
| Jina AI Remote MCP Server | 官方專案名稱 |
| jina-mcp-server | 官方文件使用的連線設定名稱 |
| Jina Reader | 將網頁或 PDF 轉成適合 AI 閱讀的文字／Markdown |
| Jina Reranker | 按照問題，重新排列文件的相關程度 |
| Jina Embeddings | 將文字轉成可比較語意的數值表示；此 MCP 用於文字語意去重 |

**記法：想讓 AI「找資料 → 讀原文 → 挑出相關內容」，就可以想到 Jina AI MCP。**

## 它是什麼？

Jina AI MCP 透過 MCP（Model Context Protocol，模型上下文協定），讓支援的 AI 客戶端呼叫 Jina AI 的網頁搜尋、內容擷取與語意處理服務。

在 ChatGPT 中，連接的 plugin 提供工具，AI 根據問題選用工具，再整理回覆。MCP 是連接 AI 與外部工具的協定；實際能做哪些事，取決於這個伺服器提供的功能。

官方遠端服務端點為 <https://mcp.jina.ai/v1>。已安裝的 ChatGPT plugin 是否需要另外設定金鑰，應以該連線介面為準。

## 功能與工具名稱對照

| 功能／用途 | 工具名稱 | 會取得或處理什麼 |
| --- | --- | --- |
| 搜尋一般網路資料 | `search_web` | 網頁標題、網址與搜尋摘要；挑選後可再讀原文 |
| 讀取網頁或 PDF | `read_url` | 擷取文字／Markdown；可帶問題挑出相關段落 |
| 查看網頁畫面 | `capture_screenshot_url` | 網頁截圖，適合查看外觀 |
| 估計文章日期 | `guess_datetime_url` | 推測發表或更新時間，附信心程度 |
| 搜尋 arXiv 論文 | `search_arxiv` | 物理、數學、資訊等領域的預印本 |
| 搜尋 SSRN 論文 | `search_ssrn` | 社會科學、經濟、法律、金融等工作論文 |
| 搜尋圖片 | `search_images` | 與查詢相關的網路圖片 |
| 搜尋 Jina 官方文章 | `search_jina_blog` | Jina AI 新聞、產品更新與技術文章 |
| 把相關文件排前面 | `sort_by_relevance` | 根據問題重新排序提供的文件 |
| 刪減語意相近的文字 | `deduplicate_strings` | 從一組文字保留較具差異的項目 |
| 擷取 PDF 圖表與公式 | `extract_pdf` | 以版面偵測擷取圖、表、公式的影像 |
| 取得時間與環境脈絡 | `primer` | 當前時間、位置與網路環境等資訊，依服務回傳為準 |

## 什麼時候適合用？

- **閱讀技術文章**：提供網址，請 AI 讀取原文，再解釋重點。
- **比較多個資料來源**：先搜尋，再閱讀候選文章，整理一致與衝突之處。
- **尋找論文**：搜尋 arXiv／SSRN，閱讀摘要與全文，檢查研究方法。
- **整理大量候選資料**：以相關性排序、語意去重，減少重複閱讀。
- **閱讀 PDF**：先擷取文字；需要圖表或公式影像時，再使用 PDF 擷取工具。

## 可以直接使用的指令例子

> 使用 Jina AI MCP 搜尋這個主題，挑三個可靠來源，讀取原文後整理重點與連結。

> 用 jina-ai-mcp 讀這篇文章，說明核心觀念、值得學的方法，以及證據不足的地方：〈貼上網址〉

> 用 Jina MCP 搜尋 arXiv 中與這個研究問題相關的論文，區分作者實際驗證的結果與推測。

> 用 Jina AI MCP 依照我的問題，將下面這些文件按相關程度排序。

這些是給 AI 的自然語言指令，不需要記住每個工具的參數名稱。

## 使用限制與判讀方式

1. **搜尋摘要適合篩選來源**：要確認主張與研究結果，仍需讀取原文。
2. **網站可能無法擷取**：登入限制、反爬蟲與動態載入可能讓結果缺漏，或只取得登入頁。
3. **帶問題的段落擷取可能漏資料**：官方文件列出表格、程式碼與「最新／第一個」等位置問題的失敗情況。查精確數字、指令或最新版本時，應核對完整原文。
4. **PDF 可能失去排版**：公式、表格與掃描文件應比對原始頁面。官方另提供 `read_url` 的逐頁 OCR 選項，是否可用須看客戶端工具參數；費用可能較高。
5. **相關性與日期都需判斷**：排序代表與問題相近；日期工具提供的是估計。
6. **工具是否好用要看實測**：這份介紹記錄功能，不宣稱優於其他搜尋工具，也沒有提供獨立 benchmark 結論。

## 金鑰、費用與版本提醒

依查核當日官方文件：

- `primer`、`guess_datetime_url`、`search_jina_blog` 無須 Jina API key。
- `read_url`、`capture_screenshot_url` 可無金鑰使用，但有速率限制；帶問題的段落排序另依金鑰與服務狀態運作，失敗時可能回傳全文。
- 一般網路搜尋、論文搜尋、圖片搜尋、相關性排序、語意去重與 PDF 圖表擷取需要金鑰。
- ChatGPT plugin 實際可用額度、驗證與計費方式，須看連線設定與服務方案；「已安裝」不能用來推定所有功能均無限制。
- 舊版教學可能列出已移除的工具，例如 `search_web_deep`、`classify_text`、`search_bibtex`。查功能時優先對照目前工具列表。

## 官方來源

- [官方 GitHub 專案與使用說明](https://github.com/jina-ai/MCP)
- [官方 README：工具列表、金鑰需求與已知限制](https://github.com/jina-ai/MCP/blob/main/README.md)
- [遠端 MCP 服務](https://mcp.jina.ai)
- [Jina Reader](https://jina.ai/reader)
- [Jina Reranker](https://jina.ai/reranker)
- [Jina Embeddings](https://jina.ai/embeddings)
- [速率限制](https://jina.ai/api-dashboard/rate-limit)
