---
title: "AI Native IDE / Code Editor 全景報告（2025-2026）"
description: "2025-2026 年 AI 原生 IDE 和 Code Editor 完整盤點——獨立 IDE、VS Code 擴充、CLI 工具、雲端 IDE、自動化 Agent"
date: 2025-04-01
slug: ai-native-ide-landscape-2025
categories:
  - ai-tools
tags:
  - IDE
  - AI
  - 工具評測
  - Cursor
  - Copilot
  - Claude Code
---

最後更新：2026-04-01

## 🖥️ 獨立 AI IDE（完整的 Editor）

| 工具 | 公司 | 開源 | 定價 | 核心特色 | 支援 Model | 狀態 |
|------|------|------|------|---------|-----------|------|
| **Cursor** | Anysphere | 否 | Free / Pro $20/mo / Biz $40/mo | VS Code fork，內建 AI chat、Tab completion、multi-file edit、Agent mode。目前最成熟的 AI IDE | GPT-4o, Claude 3.5/Opus, 自選 API key | GA |
| **Windsurf** | Codeium（被 OpenAI 收購，~$3B） | 否 | Free / Pro $15/mo | Cascade 多步驟 agent、Flows 概念，自動讀 codebase context | GPT, Claude, 自研 model | GA |
| **Trae** | ByteDance | 否 | Free (Beta) | 字節跳動出品，內建 AI chat + Builder mode，支援中文 | Claude, GPT, 豆包大模型 | Beta |
| **Zed** | Zed Industries | 是 (GPL/AGPL) | Free / Pro $10/mo (AI) | Rust 原生高效能 editor，速度極快，native collaboration，AI assistant | Claude, GPT, Ollama (本地) | GA |
| **Void** | Void Dev | 是 (MIT) | Free | 開源 AI code editor，對標 Cursor 的開源替代，支援自選 LLM | 任意（自選 API） | Alpha/Beta |
| **PearAI** | PearAI 團隊 | 是 (Apache 2.0) | Free / Pro $15/mo | 開源 AI editor，fork of Continue + VS Code，整合 AI chat 和 inline edit | Claude, GPT, 本地 model | Beta |
| **Melty** | Melty 團隊 | 是 (MIT) | Free | 主打「理解整個 codebase 變更歷史」，與 git diff 深度整合 | Claude, GPT | Alpha（可能停止活躍開發） |

## 🔌 VS Code / IDE Extension

| 工具 | 公司 | 開源 | 定價 | 核心特色 | 支援 Model | 狀態 |
|------|------|------|------|---------|-----------|------|
| **GitHub Copilot** | Microsoft/GitHub | 否 | $10/mo / Biz $19/mo / Ent $39/mo | 最廣泛使用的 AI coding tool，Copilot Chat、Agent mode、Workspace | GPT-4o, Claude, Gemini (agent) | GA |
| **Continue** | Continue Dev | 是 (Apache 2.0) | Free | 開源 AI code assistant，可接任意 LLM，高度可自訂 | 任意（OpenAI, Anthropic, Ollama） | GA |
| **Cody (Sourcegraph)** | Sourcegraph | 是（部分 Apache 2.0） | Free / Pro $9/mo / Enterprise | Codebase-aware context，利用 Sourcegraph 搜尋引擎提供精準上下文 | Claude, GPT, Gemini | GA |
| **Amazon Q Developer** | AWS | 否 | Free / Pro $19/mo | 前 CodeWhisperer，深度整合 AWS 服務，安全掃描、code transformation | 自研 (Amazon Titan+) | GA |
| **Tabnine** | Tabnine | 否 | Free / Pro $12/mo / Enterprise | 隱私優先，可完全本地部署，企業級 code completion | 自研 | GA |
| **Supermaven** | Supermaven（被 Cursor 收購） | 否 | 已整合進 Cursor | 極速 code completion（300ms），超長 context window (100K tokens) | 自研 | ⚠️ 整合進 Cursor |
| **JetBrains AI Assistant** | JetBrains | 否 | 含 JetBrains 訂閱 / $10/mo addon | 原生整合 IntelliJ 系列，AI chat + inline completion + refactor | GPT, Gemini, 自研 | GA |
| **Augment Code** | Augment | 否 | Free / Pro（定價未公開） | 大型 codebase 深度理解，企業級 context engine | Claude, GPT | GA |

## ⌨️ CLI / Terminal-based

| 工具 | 公司 | 開源 | 定價 | 核心特色 | 支援 Model | 狀態 |
|------|------|------|------|---------|-----------|------|
| **Claude Code** | Anthropic | 否 | 按 API 用量計費 | Terminal-native AI coding agent，直接讀寫檔案、執行指令、理解整個 repo | Claude 3.5/Opus | GA |
| **Aider** | Paul Gauthier | 是 (Apache 2.0) | Free | 最強 terminal AI pair programmer，支援幾乎所有 LLM，git-aware，自動 commit | 任意（GPT, Claude, Gemini, 本地） | GA |
| **GitHub Copilot CLI** | GitHub | 否 | 含 Copilot 訂閱 | Terminal 指令建議與解釋 | GPT | GA |
| **OpenAI Codex CLI** | OpenAI | 是 (Apache 2.0) | 按 API 用量 | OpenAI 官方 terminal coding agent，類似 Claude Code 定位 | GPT-4o, o3 | Beta |
| **OpenCode** | Anomaly | 是 (MIT) | Free / Zen（付費 model 代理） | 120K+ stars 的開源 AI coding agent。Terminal TUI + Desktop App + IDE Extension 三種形態。內建 Build/Plan/General/Explore 四個 agent，支援 MCP Server 擴展，LSP 整合 | 75+ 家 provider | GA |

## 🌐 Browser-based / Cloud IDE

| 工具 | 公司 | 開源 | 定價 | 核心特色 | 支援 Model | 狀態 |
|------|------|------|------|---------|-----------|------|
| **Replit** | Replit | 否 | Free / Core $25/mo | 瀏覽器全功能 IDE + AI Agent，可直接 deploy | GPT, Claude, 自研 | GA |
| **Project IDX** | Google | 否 | Free (Preview) | Google cloud IDE，整合 Firebase/GCP 和 Gemini | Gemini | Beta |
| **Bolt.new** | StackBlitz | 否 | Free / Pro $20/mo | AI 全端 web app builder，瀏覽器即時生成 + 預覽 + deploy | Claude, GPT | GA |
| **v0** | Vercel | 否 | Free / Pro $20/mo | AI UI/frontend generator，專精 React/Next.js | GPT, Claude | GA |
| **Lovable** | Lovable（前 GPT Engineer） | 否 | Free / Pro $20/mo | AI full-stack app builder，自然語言生成完整 web app | Claude, GPT | GA |

## 🤖 Autonomous Agent（全自動寫 Code）

| 工具 | 公司 | 開源 | 定價 | 核心特色 | 支援 Model | 狀態 |
|------|------|------|------|---------|-----------|------|
| **Devin** | Cognition AI | 否 | $500/mo (Team) | 第一個號稱「AI Software Engineer」，可自主規劃、寫碼、debug、deploy | 自研 + Claude/GPT | GA |
| **OpenHands** | All Hands AI（前 OpenDevin） | 是 (MIT) | Free | 開源版 Devin，自主 coding agent，有 sandbox 環境 | 任意（Claude, GPT, 本地） | GA |
| **SWE-Agent** | Princeton NLP | 是 (MIT) | Free | 學術界最強 SWE benchmark agent，GitHub issue → PR 全自動修復 | GPT, Claude | GA (研究用) |
| **Copilot Workspace** | GitHub | 否 | 含 Copilot 訂閱 | 從 GitHub Issue 到 PR 的全流程 AI 輔助 | GPT | Beta |

## 🛠️ Agent 監控 / 管理平台

| 工具 | 公司 | 開源 | 定價 | 核心特色 | 狀態 |
|------|------|------|------|---------|------|
| **OhMyAgent** | OhMyAgent.dev | 未知 | 未公開（有 Waitlist） | Multi-agent 系統的黑盒子與控制塔。四大模組：X-Ray（即時 agent 狀態流視覺化）、Human-in-the-Loop（敏感操作 breakpoint + 人類審核）、Sandbox（shadow test 環境）、Wallet Guard（per-step 成本追蹤） | Early Stage |

## 🎯 個人建議

### 現有工具鏈
- **Claude Code (via OpenClaw)** — CLI agent，已深度整合日常工作流
- **GitHub Copilot** — 日常 code completion
- **OpenClaw** — AI agent 框架，可串接多種 model

### ✅ 值得一試
- **Cursor** — GUI agent 體驗，multi-file edit 成熟，適合前端開發
- **Zed** — Rust native 高效能，適合 C/系統開發（速度快）
- **Trae** — 免費且功能完整，ByteDance 持續投入

### ⚠️ 不急著加的
- **Bolt.new / v0 / Lovable** — 專注 web app prototyping，與系統級開發場景不搭
- **Devin** — $500/mo 太貴，OpenClaw subagent 能做類似的事
- **Replit / Project IDX** — browser-based 不適合本地開發環境

### 💡 有獨特價值
- **Continue (開源)** — 可接本地 Ollama model，隱私敏感場景有價值
- **OpenHands** — 開源全自動 agent，batch 修 bug 場景可與 OpenClaw 互補

### 🆕 本次新增
- **OpenCode** — 開源 AI coding agent，有 Terminal/Desktop/IDE 三種形態，支援 75+ provider 和 MCP，Custom Agent 系統完整。跟 Claude Code 定位類似但開源且 model-agnostic
- **OhMyAgent** — Multi-agent 監控平台，提供 agent 狀態視覺化、human-in-the-loop、cost tracking。目前 early stage

---

*資料來源：截至 2025 年初知識庫 + 公開資訊 + 2026-04-01 網站查證。定價和狀態可能已有更新。*
