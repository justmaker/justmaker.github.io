---
title: "鋼琴工具與資源整理"
description: "樂譜下載、MIDI 編輯器、Synthesia 指法存檔、練習 App、線上學習資源完整整理"
date: 2025-03-06
slug: tools-resources
categories:
  - piano
tags:
  - 鋼琴
  - 工具
  - 資源
  - 樂譜
---

## 下載樂譜的方法

### 1. MuseScore
- 網站：https://musescore.com/
- 全球最大的免費樂譜分享平台

### 2. LibreScore（下載 MuseScore 譜為 PDF）
- 使用 Bookmark 方式一鍵下載
- GitHub：https://github.com/LibreScore/dl-librescore

### 3. MIDI 下載
- 透過 Discord 的 `/msdl` 指令下載
- Discord 頻道：https://discord.com/channels/1155256175609262090/1183342123794300989

## MIDI 編輯器

| 工具 | 網址 | 特色 |
|------|------|------|
| **MidiEditor** | [midieditor.org](http://www.midieditor.org) | 簡單好用，可複製貼上（注意會變成同一 track），可去尾直接存新檔 |
| **Sekaiju** | [官網](https://openmidiproject.opal.ne.jp/Sekaiju_en.html) | 日本開發，功能完整 |
| **Aria Maestosa** | [官網](https://ariamaestosa.github.io/ariamaestosa/docs/index.html) | 無法同時選取多個 track，但可以 remove measures（去頭） |
| **Ableton Live Lite** | [官網](https://www.ableton.com/en/products/live-lite/) | 專業 DAW 的入門版 |
| **FL Studio** | [官網](https://www.image-line.com/fl-studio-download/) | 另一款專業 DAW |

### MIDI 相關參考
- [MIDI 編輯器介紹文](https://m.midifan.com/article_body.php?id=7309)

## 音訊裁切

- **Audacity**：https://www.audacityteam.org/
- 免費開源的音訊編輯軟體，可裁切、合併、調整音量等

## Synthesia 指法存檔

[Synthesia](https://www.synthesiagame.com/) 是很好的鋼琴練習軟體，但指法紀錄的備份需要特別處理：

### 電腦版

1. **找到本地數據**：
   - 按住 Shift 鍵啟動 Synthesia → 出現「Open Data Folder」
   - 或手動到 `C:\Users\你的用戶名\AppData\Roaming\Synthesia`
   - 指法資訊存在 `fingers.xml` 或類似檔案中

2. **使用 Metadata Editor**：
   - GitHub：https://github.com/Synthesia-LLC/metadata-editor
   - File → Import data from Synthesia
   - 選擇匯入 finger hints and hand assignments
   - Save/Export 為 `.synthesia` 檔案
   - 將檔案與 MIDI 檔放在同一目錄

### 平板版

- ⚠️ 從平板到電腦的指法匯出**不支援**（除非越獄）
- 但從電腦到平板可以用 Metadata Editor 匯出 `.synthesia` 檔案再傳到平板
- 建議**定期備份** `AppData\Roaming\Synthesia` 資料夾

## 製作工具

| 工具 | 用途 |
|------|------|
| Mac Logic Pro | 專業音樂製作 |
| Mac GarageBand | 入門音樂製作、[教學影片](https://youtu.be/a6gfUHf34LE) |
| Mac Final Cut Pro | 影片剪輯 |

## 線上打譜

- **Noteflight**：https://www.noteflight.com/guide
  - 線上樂譜編輯，三連音按 `3`

## 線上學習資源

- [林有龍鋼琴教學](https://www.youtube.com/watch?v=Rn6NGrw0OaY&ab_channel=%E6%9E%97%E6%9C%89%E9%BE%8D)
- [鋼琴工具推薦](https://youtu.be/2ueyqx4rDCM)
- [PTT 鋼琴版推薦文](https://www.ptt.cc/bbs/piano/M.1602845278.A.C14.html)
- [10 個免費鋼琴譜網站推薦](https://pianoroomno1.wordpress.com/2017/10/23/10%E5%80%8B%E5%85%8D%E8%B2%BB%E9%8B%BC%E7%90%B4%E8%AD%9C%E7%B6%B2%E7%AB%99%E6%8E%A8%E8%96%A6%EF%BC%81/)
- [手指獨立練習 1](https://www.youtube.com/watch?v=N8Sz2ll8NpU)
- [手指獨立練習 2](https://www.youtube.com/watch?v=YOz-GyTpvyk)
- [手指獨立練習 3](https://www.youtube.com/watch?v=uwfzzKAXyos)
