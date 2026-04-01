---
title: "個人知識庫/部落格平台評估"
description: "WordPress、Notion、Hugo + GitHub Pages 三大平台完整比較——哪個最適合放知識、讓人逛到、有討論功能？"
date: 2025-03-30
slug: blog-platform-evaluation
categories:
  - devops
tags:
  - 部落格
  - 平台評估
  - hugo
  - wordpress
  - notion
---

## 需求

- **放知識和興趣** — 長期內容庫
- **別人能逛到** — 公開、SEO 友好
- **有討論功能** — 留言/評論
- **AI 能大量寫文章** — API 友好、自動化方便

## AI（OpenClaw）能操控的平台

| 平台 | 能操作？ | 方式 |
|------|---------|------|
| WordPress | ✅ | REST API（`/wp-json/wp/v2/posts`），建立/編輯/發布/上傳媒體 |
| Notion | ✅ | Notion API（需 integration token） |
| Hugo + GitHub Pages | ✅ | git push markdown，自動 build |
| Confluence | ✅ 已在用 | REST API |
| Medium | ⚠️ 有限 | API 可發文但功能受限 |
| Substack | ❌ | 沒有公開 API |

## 平台比較

| 面向 | WordPress | Notion | Hugo + GitHub Pages |
|------|-----------|--------|-------------------|
| 公開 SEO | ✅ 最強，Google 天然友好 | ⚠️ 可公開但 SEO 差 | ✅ 不錯 |
| 別人討論 | ✅ 內建留言 + Disqus | ❌ 只能 comment | ⚠️ 要外掛（Giscus/Disqus） |
| AI 操作方便度 | ✅ REST API 完整 | ✅ API 完整，結構化好 | ✅ git push markdown 最方便 |
| 大量文章 | ✅ 天生為此設計 | ✅ database view | ✅ 檔案系統 |
| 費用 | 🟡 自架免費要 server | 🟢 免費 | 🟢 完全免費 |
| 外觀自訂 | ✅ 無限 theme + CSS | ⚠️ 有限 | ✅ 完全自訂 |
| 維護成本 | 🟡 要更新 + 安全 | 🟢 零維護 | 🟢 零維護 |

## AI 操作方便度排名

1. 🥇 **Hugo + GitHub Pages** — git push markdown，最直覺
2. 🥈 **WordPress REST API** — 一個 curl 搞定，可批量
3. 🥉 **Notion API** — 結構化好但 block-based 寫法較囉嗦

## 建議

- 如果目標是「別人逛得到 + 有討論」→ **WordPress** 最適合
  - SEO 最強，Google 搜得到
  - 留言系統內建
  - REST API 一個 POST 就發文，可排程批量
- 如果只是個人知識庫、不在意 SEO → **Notion** 更簡單
- 如果偏好工程師風格 markdown → **Hugo + GitHub Pages + Giscus 留言**

## 結論

最終選了 **Hugo + GitHub Pages**：

- 完全免費、零維護
- Markdown 寫作，工程師友善
- Git 版本控制，每篇文章的修改歷史清楚
- 搭配 AI agent（OpenClaw）可以直接 git push 發文，自動化最方便
- 加上 Giscus 就有留言功能
- SEO 表現不錯，配合 sitemap + Google Search Console 夠用
