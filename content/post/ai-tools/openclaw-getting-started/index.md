---
title: "用 OpenClaw 打造 AI 助理：從零開始"
description: "OpenClaw 入門教學——安裝、設定、連接 Discord，打造你的專屬 AI 助理"
date: 2025-04-04
slug: openclaw-getting-started
categories:
  - ai-tools
tags:
  - openclaw
  - ai
  - 教學
---

## 什麼是 OpenClaw？

[OpenClaw](https://github.com/openclaw/openclaw) 是一個開源的 AI agent 框架，可以讓 LLM（如 Claude、GPT）不只是聊天，還能實際操作你的電腦：讀寫檔案、執行指令、管理 Git、呼叫 API。

它不是另一個 ChatGPT 包裝，而是一個**能幹活的 AI 助理**。

## 核心概念

### Agent ≠ Chatbot

一般 chatbot 只能接收文字、回覆文字。OpenClaw 的 agent 可以：

- 📁 讀寫你的檔案系統
- 🖥️ 執行 shell 指令
- 🔧 操作 Git（commit、push、建 MR）
- 🌐 瀏覽網頁、呼叫 API
- 📱 連接 Discord / Telegram 接收訊息
- 🧠 記住對話脈絡（透過 MEMORY.md）

### Workspace 結構

```
~/.openclaw/workspace/
├── AGENTS.md      # Agent 行為規範
├── SOUL.md        # Agent 的個性設定
├── USER.md        # 關於你的資訊
├── TOOLS.md       # 可用工具說明
├── IDENTITY.md    # Agent 的身份
├── TODO.md        # 待辦事項
└── MEMORY.md      # Agent 的記憶
```

這些 `.md` 檔案就是 agent 的「大腦」——每次啟動時讀取，形成行為模式。

## 能做什麼？

以我日常使用為例：

### 自動化開發
> 「幫我寫一個 KVM 效能監控腳本，放到 ~/scripts/ 裡」

Agent 會直接寫好腳本、設定執行權限、甚至幫你加到 crontab。

### 知識管理
> 「把今天 Discord #ai-tools 頻道的討論整理成一篇部落格文章」

Agent 讀取 Discord 訊息、整理成結構化文章、push 到 Hugo 部落格。

### 程式碼審查
> 「Review 一下最新的 MR」

Agent 會讀 MR diff、分析問題、留下 review comment。

## 適合誰？

- 工程師、開發者（最大受益者）
- 需要自動化重複工作的人
- 願意花時間調教 AI 行為的人

## 下一步

如果你對 OpenClaw 感興趣，可以到 [GitHub repo](https://github.com/openclaw/openclaw) 看看文件和範例。

後續文章會深入介紹進階功能：MCP server 串接、多 agent 協作、自動化工作流。
