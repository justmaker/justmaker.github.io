---
title: "與 AI 協作的開發工作流：Coding、Debug、Code Review、規格維護與前端整合"
description: "不只是叫 AI 寫 code — 一套可落地的完整工作流，涵蓋專案脈絡設定、四段式開發、Debug 流程、雙軌 Code Review、規格防腐與前端視覺驗證迴路"
date: 2026-08-31
slug: ai-collab-workflow
categories:
  - ai-tools
tags:
  - AI
  - 工作流
  - Code Review
  - Debug
  - 規格
  - 前端
---

# 與 AI 協作的開發工作流

前一篇[《AI 使用技巧、經驗與避坑指南》](/post/ai-tools/ai-tips-and-pitfalls/)談的是 prompt 層級的技巧。但真正決定產出品質的，其實是**工作流層級**的設計 — 你怎麼餵脈絡、怎麼切任務、怎麼驗證、怎麼讓文件不腐爛。

這篇就是把那一整套寫下來。

---

## 0. 核心心智模型

AI 不是「會寫程式的人」，是**高速但沒有記憶、沒有責任感的實習生**。

整套工作流的設計原則只有三條：

1. **上下文要用檔案供給，不要用對話供給** — 對話會消失，檔案不會
2. **每一步都要有可驗證的產出** — 測試、build、screenshot、diff
3. **人類守住決策點，AI 負責產出量**

---

## 1. 專案骨架：讓 AI 每次都「醒來就懂」

在 repo root 放這幾個檔案，任何 AI 工具（Claude Code / Copilot / Cursor / OpenClaw）都吃得到：

```text
repo/
├── AGENTS.md          # 給 AI 的專案守則（架構、慣例、禁區、指令）
├── docs/
│   ├── spec/          # 規格書（單一事實來源）
│   ├── adr/           # 架構決策紀錄 ADR-0001.md ...
│   └── runbook.md     # 怎麼跑起來、怎麼測、怎麼部署
└── .ai/
    ├── prompts/       # 可重用的 prompt 樣板
    └── context.md     # 當前迭代的暫存脈絡（每個 sprint 更新）
```

**AGENTS.md 至少要寫：**

- 技術棧與版本（含 lint / formatter 規則）
- 目錄職責（哪層可以改、哪層碰了要先問）
- 驗證指令（`npm test` / `make lint` / `pnpm build`）
- 紅線（不要動 migration、不要改 public API、不要自己裝套件）
- Commit / PR 慣例

這一步做完，AI 的產出品質大概會跳一個級距。**比任何 prompt 技巧都有效。**

---

## 2. 寫程式：Spec → Plan → Diff → Verify

不要直接說「幫我做 X 功能」。改成四段式：

### ① Spec（人主導）

先讓 AI 幫你把需求寫成規格，你來審。

> 「把這段需求整理成規格：使用者故事、驗收條件（Given/When/Then）、邊界條件、不做的事。有歧義的地方列成問題清單，**不要自己假設**。」

那份「問題清單」是精華 — 通常會抓到你自己沒想到的洞。

### ② Plan（AI 提案、人核可）

> 「讀 `src/` 相關檔案，提出實作計畫：要改哪些檔、每個檔改什麼、風險在哪、測試怎麼寫。**先不要寫 code。**」

看到計畫不對就在這裡擋掉。**在 plan 階段修正的成本是 code 階段的 1/10。**

### ③ Diff（AI 執行、小步）

一次一個關注點。經驗值：單次改動 **< 300 行、< 5 個檔**。

超過就拆。太大的 diff 你不會認真看，AI 也會開始亂編。

### ④ Verify（機器判定）

每個 diff 後強制跑：`lint → typecheck → test → build`。

把這串包成一個指令（`make check`），讓 AI 自己跑、自己修到綠。

**沒有綠燈的產出等於沒有產出。**

---

## 3. Debug：把 AI 當「假設產生器」，不是「答案產生器」

AI 猜 bug 原因很快，但很愛自信地猜錯。流程要這樣走：

1. **給證據，不給敘述** — 貼完整 stack trace、實際 input、失敗的測試輸出。不要寫「它壞掉了」。
2. **要求列假設而非答案**
   > 「列出 5 個可能原因，依可能性排序，每個附上『我該怎麼驗證它』的具體指令。」
3. **先寫重現測試** — 在修之前，讓 AI 寫一個會 fail 的測試。修好 = 測試變綠。這樣就不會有「好像好了」。
4. **二分法搜尋** — 讓 AI 提出插 log 的位置或 `git bisect` 範圍，你跑，把結果餵回去。
5. **修完問一句** — 「這個 root cause 還可能出現在其他地方嗎？」常常會撈到同類 bug。

### 避坑

- ❌ 讓 AI 在沒看到實際錯誤輸出的情況下改 code（它會開始改無關的東西）
- ❌ 連續三次修不好還繼續讓它試 — 這時它已經在亂猜，**回到第 1 步重新給脈絡**
- ❌ 接受「加個 try/catch 包起來」這種修法

---

## 4. Code Review：雙軌制

### 軌道 A — AI review 人類的 code

用固定的 review checklist prompt（存在 `.ai/prompts/review.md`）：

> 角色：資深 reviewer。針對這份 diff 檢查：正確性 / 邊界條件 / 錯誤處理 / 併發與競態 / 效能熱點 / 安全（injection、authz、secret）/ 測試覆蓋 / 是否違反 AGENTS.md。
>
> 每則意見標 **blocker / should / nit**，並附建議改法。**找不到問題就說沒有，不要湊數。**

最後那句很重要，不然它會為了顯得有用而製造假問題。

### 軌道 B — 人類 review AI 的 code

AI 產的 code 要用**更嚴格**的標準看，重點看它最會犯錯的地方：

- 幻覺 API / 不存在的套件方法
- 錯誤處理被吞掉
- 「看起來對」但邊界條件錯（off-by-one、空陣列、null）
- 測試是照著實作寫的（同義反覆，測不出東西）
- 悄悄改了不該改的地方

**每次都看完整 diff，不要只看它的摘要。**

---

## 5. 規格維護：讓文件不會腐爛

規格會爛，是因為改 code 時沒人改文件。做法：

- **Spec 進 repo** — 跟 code 同一個 PR 一起改。文件不在 repo 就一定會爛。
- **PR 模板加一欄** — 「本次是否影響 `docs/spec/`？是 → 附上 diff；否 → 說明理由」
- **定期漂移檢查**（每個 sprint 或 CI 週跑一次）
  > 「比對 `docs/spec/payment.md` 與 `src/payment/`，列出：規格有但沒實作、實作有但規格沒寫、兩邊描述矛盾的地方。」

  這招意外好用，通常一跑就一堆。
- **決策寫 ADR** — 為什麼選 A 不選 B、當時的限制是什麼。半年後你和 AI 都會需要。三段就好：Context / Decision / Consequences。
- **規格用 Given/When/Then 寫** — 因為它可以直接對應到測試，AI 也能直接轉成 test case。

---

## 6. 前端整合：AI 最容易「看起來對」的區域

前端的坑在於**編譯過 ≠ 畫面對**。要補上視覺驗證迴路：

- **契約先行** — 先定 OpenAPI / TypeScript type，前後端都從它生成。讓 AI 改 API 時同步改契約檔，型別錯誤自然會炸出來。
- **給設計稿截圖**，不要用文字描述 UI。多模態模型看圖的效果遠勝於「一個置中的卡片，圓角 8px…」
- **Playwright 當 AI 的眼睛** — 讓 AI 自己跑 headless browser 截圖 → 自己看 → 自己修。**這是前端 AI 協作品質的分水嶺。**
- **元件層開發** — Storybook 或獨立 route，讓 AI 在隔離環境迭代單一元件，不要一次動整頁。
- **狀態管理明確化** — 告訴它資料流方向與狀態放哪。不然它會在每個元件塞 `useState`，然後你就有一堆同步 bug。
- **必檢清單** — loading / empty / error 三態、RWD 斷點、a11y（label、對比、鍵盤）、i18n 字串沒 hardcode。**AI 預設全都會漏。**

---

## 7. 一個可以照抄的日常循環

```text
早上   → 更新 .ai/context.md（今天要做什麼、卡在哪）

任務   → Spec → 問題清單 → 人拍板
       → Plan → 人核可
       → 分成 3~5 個小 diff

每 diff → AI 實作 → make check 綠 → 人看完整 diff → commit

完成   → AI 自審（review prompt）→ 人開 PR
       → 同步更新 spec / ADR

週末   → 規格漂移檢查 + 清理 .ai/context.md
```

---

## 8. 心法濃縮

- **上下文 > 模型 > prompt 技巧** — 花時間整理 AGENTS.md 的回報率最高
- **小步快跑** — 大 diff 是所有 AI 協作災難的共同起點
- **驗證要交給機器** — 人類的注意力留給「方向對不對」，不是「語法對不對」
- **AI 沒有記憶，檔案有** — 任何你希望它下次還記得的事，寫進檔案
- **連續失敗 = 脈絡不足**，不是模型太笨。停下來補脈絡，別硬催
- **保留你的判斷力** — 可以讓 AI 寫，但你要看得懂。**看不懂的 code 不要 merge**

---

## 延伸閱讀

- [AI 使用技巧、經驗與避坑指南](/post/ai-tools/ai-tips-and-pitfalls/) — Prompt 層級的技巧
- [Claude Code vs GitHub Copilot：工程師實測比較](/post/ai-tools/claude-code-vs-github-copilot/) — 工具選擇
- [AI 工具 KB 總索引](/post/ai-tools/knowledge-map/) — 整區導覽
