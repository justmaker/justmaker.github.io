---
title: "Hugo + GitHub Pages 建站踩坑紀錄"
description: "建這個站過程中遇到的問題和解決方法——省下你的 debug 時間"
date: 2025-04-06
slug: hugo-github-pages-pitfalls
categories:
  - devops
tags:
  - hugo
  - github-pages
  - 踩坑紀錄
---

## 前言

建這個站的過程其實沒有想像中順利。這篇記錄我遇到的坑，希望能幫其他人省點時間。

## 坑 1：Hugo 版本不對

### 問題
用 `apt install hugo` 裝的版本太舊（0.68），很多新 theme 需要 0.110+。

### 解法
直接從 GitHub Release 下載 extended 版：
```bash
wget https://github.com/gohugoio/hugo/releases/download/v0.147.0/hugo_extended_0.147.0_linux-amd64.deb
sudo dpkg -i hugo_extended_0.147.0_linux-amd64.deb
```

**一定要用 extended 版**，不然 SCSS 編譯會失敗。

## 坑 2：GitHub Actions 的 submodule

### 問題
Theme 是用 `git submodule add` 加的，但 GitHub Actions checkout 時預設不會 clone submodule，導致 build 時找不到 theme。

### 解法
`actions/checkout` 加上 `submodules: recursive`：
```yaml
- uses: actions/checkout@v4
  with:
    submodules: recursive
    fetch-depth: 0
```

## 坑 3：GitHub Pages Source 設定

### 問題
Push 上去後 GitHub Pages 顯示 404。

### 解法
到 repo **Settings → Pages → Build and deployment → Source**，選 **GitHub Actions**（不是 Deploy from a branch）。

很多教學文寫的是舊版用法（gh-pages branch），現在推薦用 GitHub Actions。

## 坑 4：baseURL 結尾斜線

### 問題
`baseURL` 沒加結尾 `/`，導致部分資源路徑錯誤。

### 解法
```yaml
# ✅ 正確
baseURL: https://justmaker.github.io/

# ❌ 錯誤
baseURL: https://justmaker.github.io
```

## 坑 5：中文檔名和 URL

### 問題
中文標題預設會變成中文 URL（`/post/我的文章/`），在某些環境下會出問題。

### 解法
每篇文章都明確指定 `slug`：
```yaml
---
title: "我的中文標題"
slug: my-english-slug
---
```

## 坑 6：搜尋功能不 work

### 問題
Stack theme 的搜尋功能一直轉圈。

### 解法
需要在 `hugo.yaml` 的 `outputs` 加上 `JSON`：
```yaml
outputs:
  home:
    - HTML
    - RSS
    - JSON    # ← 搜尋功能需要這個
```

Stack theme 的搜尋是 client-side，靠 `index.json` 做全文搜尋。

## 總結

大部分坑都是設定問題，知道就很簡單，不知道要 debug 很久。希望這篇能幫到你。

如果你也遇到其他坑，歡迎在下方留言分享 👇
