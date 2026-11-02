# Superpowers：AI 開發流程與技能名稱速查

查核日期：2026-11-02。依上游官方 README、skills 目錄與當次連線提供的技能名稱整理；不同平台、版本與工作區設定可能影響實際行為。

## 名稱速查

| 搜尋名稱／別稱 | 對應內容 |
| --- | --- |
| Superpowers、Superpowers plugin、superpowers | 提供 AI 開發流程的一組可組合技能 |
| obra/superpowers | 上游官方 GitHub 儲存庫 |
| Jesse Vincent、Prime Radiant | 官方 README 列出的作者與團隊 |
| superpowers:brainstorming 等名稱 | plugin 名稱與個別 skill 名稱的組合；實際顯示方式依平台而異 |
| SKILL.md | 各技能的操作說明與流程規則 |

**記法：要 AI 先釐清需求、規劃、循序開發、找錯與驗證，可以想到 Superpowers。**

## 它是什麼？

Superpowers 把軟體開發方法寫成 AI 能讀取的技能：從需求討論、計畫、測試、除錯，到審查與分支收尾。Plugin 負責包裝與整合這些技能，個別 skill 則負責特定階段的工作流程。

它主要約束 AI 如何工作。實際讀寫 GitHub、執行測試、建立分支或派遣子代理，仍需要目前環境提供對應工具與權限。安裝後也不能保證 AI 每次都正確遵守流程。

## 依技能名字查功能

下列 15 個名稱同時出現在查核當日的上游 skills 目錄與本次連線技能清單。點擊名稱可讀上游原始說明。

| 技能名稱 | 中文功能 | 適合何時使用 |
| --- | --- | --- |
| [brainstorming](https://github.com/obra/superpowers/blob/main/skills/brainstorming/SKILL.md) | 釐清目標、需求、限制與設計方案 | 想法還模糊，或動工前要先確認方向 |
| [writing-plans](https://github.com/obra/superpowers/blob/main/skills/writing-plans/SKILL.md) | 把已確認的設計拆成可執行步驟，列出修改與驗證方式 | 已決定要做什麼，準備安排工作 |
| [executing-plans](https://github.com/obra/superpowers/blob/main/skills/executing-plans/SKILL.md) | 依既有計畫執行工作 | 計畫已核准，準備開始實作 |
| [subagent-driven-development](https://github.com/obra/superpowers/blob/main/skills/subagent-driven-development/SKILL.md) | 交由子代理逐項實作，再檢查規格符合度與程式品質 | 多步驟開發，環境支援子代理 |
| [dispatching-parallel-agents](https://github.com/obra/superpowers/blob/main/skills/dispatching-parallel-agents/SKILL.md) | 把互相獨立的工作交給多個代理並行處理 | 幾個問題能分開調查，且不會互相修改衝突 |
| [test-driven-development](https://github.com/obra/superpowers/blob/main/skills/test-driven-development/SKILL.md) | 測試驅動開發：先觀察測試失敗，再寫最少程式通過，最後重構 | 新增行為或修復錯誤，需要可重現的驗證 |
| [systematic-debugging](https://github.com/obra/superpowers/blob/main/skills/systematic-debugging/SKILL.md) | 系統化除錯：蒐集證據、找規律、驗證假設，再修復根因 | 程式出錯、測試失敗或行為不如預期 |
| [verification-before-completion](https://github.com/obra/superpowers/blob/main/skills/verification-before-completion/SKILL.md) | 在宣告完成或修好之前，取得實際驗證證據 | AI 說「完成了」前，要確認檢查結果 |
| [requesting-code-review](https://github.com/obra/superpowers/blob/main/skills/requesting-code-review/SKILL.md) | 安排程式碼審查，檢查需求與品質問題 | 完成重要修改，準備合併前 |
| [receiving-code-review](https://github.com/obra/superpowers/blob/main/skills/receiving-code-review/SKILL.md) | 理解與驗證審查意見，再決定如何修改 | 收到 review，需要判斷建議是否正確 |
| [using-git-worktrees](https://github.com/obra/superpowers/blob/main/skills/using-git-worktrees/SKILL.md) | 用 Git worktree 建立隔離工作目錄 | 希望不同分支各有自己的工作目錄 |
| [finishing-a-development-branch](https://github.com/obra/superpowers/blob/main/skills/finishing-a-development-branch/SKILL.md) | 檢查完成狀態，處理合併、PR、保留或清理分支的選擇 | 開發結束，準備交付與收尾 |
| [diagnosing-superpowers](https://github.com/obra/superpowers/blob/main/skills/diagnosing-superpowers/SKILL.md) | 檢查 Superpowers 在對話中的流程問題，提供紀錄證據 | 技能沒觸發、錯誤觸發、反覆做事或用量異常 |
| [writing-skills](https://github.com/obra/superpowers/blob/main/skills/writing-skills/SKILL.md) | 撰寫、修改及驗證技能說明 | 想把可重複流程整理成 skill |
| [using-superpowers](https://github.com/obra/superpowers/blob/main/skills/using-superpowers/SKILL.md) | 說明如何發現與使用適用技能 | 理解整套技能系統如何啟動 |

注意：上游目前把 executing-plans 描述為在主要對話中逐項執行，最後安排一次整體審查；舊版本或已安裝版本的細節可能不同。實際執行時應讀取當前載入的 SKILL.md。

## 從需求反查名字

| 我現在需要…… | 先找這個技能 |
| --- | --- |
| 先討論清楚，暫時不要動工 | brainstorming |
| 把討論結果整理成步驟與驗收 | writing-plans |
| 找出 bug 的原因 | systematic-debugging |
| 確認 AI 真的修好了 | verification-before-completion |
| 檢查別人或 AI 寫的修改 | requesting-code-review |
| 評估收到的修改建議 | receiving-code-review |
| 調查 Superpowers 自己的使用問題 | diagnosing-superpowers |

brainstorming 也可協助整理一般決策的目標與限制；Superpowers 的主要設計場景仍是軟體開發，求職、醫療等領域的事實查核需要另外處理。

## 可以直接複製的使用範例

以下是提示詞範例，本次沒有逐一執行或評測。可先在介面選取 Superpowers plugin，再指定技能名稱；名稱文字本身不能保證平台已載入技能。

### 1. 先釐清需求

> 使用 Superpowers 的 brainstorming，協助我釐清待辦事項 API 的使用情境。一次問一個問題，最後整理最小功能與驗收條件。先討論，不修改檔案；實作前另行取得我的明確同意。

### 2. 整理實作計畫

> 使用 writing-plans，把已確認的 API 規格拆成小步驟，列出每步要修改的檔案、理由與驗收方式。先交付計畫供我檢查。

### 3. 查明錯誤原因

> 使用 systematic-debugging 調查這個失敗的測試。先重現、列出證據與假設，再用最小實驗確認原因。說明預計修正範圍，待我確認後再修改程式。

### 4. 確認完成的證據

> 使用 verification-before-completion 檢查這次修改。列出實際執行的驗證、結果及尚未確認的部分。沒有執行的項目請明說。

### 5. 評估審查建議

> 使用 receiving-code-review 檢查這份 review。逐項核對建議是否符合需求與現有程式，附上判斷依據，先給我評估結果。

### 6. 檢查技能運作問題

> 使用 diagnosing-superpowers，分析這段對話為什麼反覆規劃、沒有往前進。引用可取得的對話證據，說明可能原因與改善方式；缺少紀錄時請明說。

## 一般開發流程

可把它記成幾個階段：

1. 用 brainstorming 確認需求與設計。
2. 視需要用 using-git-worktrees 準備工作目錄，再用 writing-plans 拆解步驟。
3. 取得實作授權後，以 executing-plans 或 subagent-driven-development 執行。
4. 開發過程依工作需要使用測試、除錯與審查技能。
5. 用 verification-before-completion 確認證據，再由 finishing-a-development-branch 協助收尾。

具體順序、審查次數及產出檔案依載入版本與專案規則而異。使用者應明確指定哪些階段只討論、哪些階段允許修改，以及提交、推送與合併的範圍。

## 使用限制與成本

- **可用工具影響能力**：沒有終端機、Git 或子代理工具時，相關流程只能部分執行；對話中模擬不同角色，也無法取代實際獨立代理的執行紀錄。
- **流程需要時間與用量**：讀技能、寫計畫、跑測試與多次審查都會增加工作量；多代理不保證每次更快或更便宜。
- **成果仍需驗收**：測試可能缺漏，審查也可能出錯。可要求提供修改差異、實際測試結果與已知限制。
- **額度依使用平台為準**：上游採 MIT 授權；模型、訂閱、執行環境與其他服務的費用仍需另計，本文沒有評估特定方案價格。
- **安裝與版本依平台而異**：官方 README 提供多種環境的安裝方式。在一個環境安裝，不代表其他環境也已安裝；本篇未核對讀者自己的安裝來源。
- **操作仍需符合授權**：技能建議建立檔案、提交或合併時，要連同使用者指示及儲存庫規則判斷，不能把技能名稱當成所有操作的授權。

## 官方來源與查核範圍

- [上游官方儲存庫與 README](https://github.com/obra/superpowers)
- [官方技能目錄](https://github.com/obra/superpowers/tree/main/skills)
- [官方使用入口：using-superpowers](https://github.com/obra/superpowers/blob/main/skills/using-superpowers/SKILL.md)

本文核對官方 README、技能目錄與當次連線列出的 15 個技能名稱，並讀取當前 using-superpowers 說明。未逐一實測全部技能，也沒有提出成功率或效率提升的 benchmark。上表各技能附有原始說明連結，執行時應以當前安裝版本為準。
