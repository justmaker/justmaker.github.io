---
title: "為什麼我要建這個知識庫"
description: "用 Hugo + GitHub Pages 打造個人技術部落格的動機與規劃"
date: 2025-04-01
slug: hello-world
categories:
  - devops
tags:
  - hugo
  - github-pages
  - 心得
---

## 動機

工作幾年下來，技術筆記散落在各處——Confluence 頁面、Discord thread、各種 markdown 檔案、甚至腦子裡。每次要找之前踩過的坑，得翻半天。

是時候把這些東西整理成一個對外的知識庫了。

## 為什麼選 Hugo + GitHub Pages？

考慮過幾個方案：

| 方案 | 優點 | 缺點 |
|------|------|------|
| WordPress | 功能完整、外掛多 | 需要主機、慢、維護成本高 |
| Notion | 寫起來舒服 | SEO 差、客製化有限 |
| Hexo | 靜態、Markdown | Node.js 生態，build 慢 |
| **Hugo** | **極快 build、Go 寫的、生態成熟** | 模板語法學習曲線 |

最終選了 Hugo + GitHub Pages：

- **免費託管**，不用管主機
- **Markdown 寫作**，工程師友善
- **Build 速度極快**，幾百篇文章也是秒 build
- **搭配 AI agent** 可以批量產出內容
- **Git 版本控制**，每篇文章的修改歷史一清二楚

## 內容規劃

這個站會涵蓋我的主要興趣和工作領域：

### 🖥️ 虛擬化技術
KVM、QEMU——這是我的主戰場。從架構設計到效能調校，踩過的坑多到可以寫一本書。

### 🤖 AI 開發工具
OpenClaw、Claude、Copilot 的使用心得和實戰經驗。AI 輔助開發已經是我日常工作流的一部分。

### ⚫ 圍棋
業餘愛好，偶爾記錄覆盤心得和學習筆記。

### 🎹 鋼琴
練琴心得和曲目紀錄。

### 🏓 桌球
業餘打球的紀錄和技術筆記。

## 技術架構

```
Hugo (靜態網站產生器)
  + Stack theme (UI)
  + GitHub Pages (託管)
  + GitHub Actions (自動部署)
  + Giscus (留言系統)
  + OpenClaw (AI 輔助寫文)
```

整個流程：寫 Markdown → push 到 GitHub → Actions 自動 build → 部署到 GitHub Pages。

## 接下來

先把幾篇核心文章寫出來，建立內容基底。然後慢慢養成定期發文的習慣。

目標是每週 1-2 篇，有 AI 幫忙應該不難。

敬請期待 🚀
