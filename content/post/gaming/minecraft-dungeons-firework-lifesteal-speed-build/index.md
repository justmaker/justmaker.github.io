---
title: "Minecraft Dungeons 連發火箭吸血速攻流：豎琴弩、凋零盔甲與鬥士護手終極配置"
description: "以連發煙火、全攻擊回血、高速近戰為優先順序，整理豎琴弩、凋零盔甲、鬥士護手的畢業附魔、法器、掉落地圖與遠古狩獵符文，並逐項核實常見錯誤。"
date: 2026-09-24T11:21:00+08:00
lastmod: 2026-09-24T11:21:00+08:00
draft: false
categories:
  - gaming
tags:
  - Minecraft Dungeons
  - 攻略
  - Build
  - 煙火流
  - 吸血流
image: ""
---

> 🧭 [回到 Minecraft Dungeons KB 總索引](/post/gaming/minecraft-dungeons-knowledge-map/)

這套 Build 的需求優先順序是：**連發煙火 > 近戰與遠程都能回血 > 高速近戰**。核心組合為 **豎琴弩＋凋零盔甲＋鬥士護手**，利用豎琴弩一次五發的特性擴大煙火之箭，靠凋零盔甲的 6% 吸血同時支援遠程與近戰，最後用毒帽菇把鬥士護手推進高速連打狀態。

這是「三項需求兼顧」的終極配置，不代表純煙火傷害最高的極端配法。若完全不在乎近戰與生存，三個煙火之箭配多重冷卻會有更密集的爆發；本篇則保留毒帽菇和吸血體系。

## 終極配置速查

### 盔甲：凋零盔甲（Wither Armor）

固定屬性為 **35% 傷害減免、+50% 靈魂收集、6% 吸血光環**。數值與普通掉落池可由 [Minecraft Wiki：Wither Armor](https://minecraft.wiki/w/Dungeons:Wither_Armor) 核實。

**一般三附魔：**

1. **冷卻（Cool Down）**：縮短煙火之箭與毒帽菇的 30 秒冷卻。
2. **冷卻（Cool Down）**：第二層冷卻是火箭輪替能否順暢的關鍵。
3. **偏轉（Deflect）**或**藥水護盾（Potion Barrier）**：前者處理遠程彈幕，後者提供喝藥後的緊急減傷。

**理想鍍金附魔：**

- **藥水護盾**：最泛用的保命選擇。
- **冷卻**：火箭密度優先的極限版本；再透過附魔師重洗一般欄位，才可能形成多重冷卻。

[冷卻 III](https://minecraft.wiki/w/Dungeons:Cool_Down) 每層降低 38% 法器冷卻，而且可堆疊；[藥水護盾 III](https://minecraft.wiki/w/Dungeons:Potion_Barrier) 則在喝藥後提供 9 秒的 90% 減傷。冷卻堆疊不是把百分比直接相加成零冷卻，因此仍無法保證真正無空窗。

### 遠程：豎琴弩（Harp Crossbow）

[豎琴弩](https://minecraft.wiki/w/Dungeons:Harp_Crossbow) 每次射擊會放出五枚投射物，而且每一枚都能獨立判定遠程附魔，是煙火流的核心發射台。

**一般三附魔：**

1. **無盡（Infinity）**：III 級有 48% 機率不消耗當前箭矢，也適用煙火箭等特殊箭矢。
2. **多重射擊（Multishot）**：五枚基礎投射物各自有 40% 機率分裂成五枚，全部觸發時理論上可達 25 枚。
3. **連鎖反應（Chain Reaction）**：命中時有 30% 機率向周圍射出五枚額外箭矢，強化大群清場。

**理想鍍金附魔：**

- **力量（Power）**：最直觀、穩定的遠程增傷。
- **穿透（Piercing）**：讓箭矢繼續命中後方敵人，適合狹長通道與密集怪群；實際爆炸位置會因穿透而改變，手感不一定優於力量。

不把**虛空打擊**列為首選，因為它的倍率需要時間上升，而且同一把武器再次命中會重設倍率；豎琴弩是五發齊射的高速武器，與此機制衝突。可查 [Minecraft Wiki：Void Strike](https://minecraft.wiki/w/Dungeons:Void_Strike) 的重設規則。

> **重要限制：** 無盡 III 是 48% 機率免耗，不是保證無限。單次裝填煙火後，連續射擊的理論平均值約為 1.92 次；因此要靠兩個煙火法器與多重冷卻縮短空窗，而不是把「無盡」理解成永久連射。

### 近戰：鬥士護手（Fighter's Bindings）

[鬥士護手](https://minecraft.wiki/w/Dungeons:Fighter%27s_Bindings) 是四段、幾乎沒有連擊間隔的高速武器，每第四拳都算連擊終結，所以能頻繁觸發旋風與震撼。該條目也記錄了 1.16.2.0 版本曾把攻擊間隔從 0.125 秒調整為 0.15 秒，因此不採用「固定每秒 7.14 拳」這種未標版本的說法。

**推薦一般三附魔：**

1. **旋風（Swirling）或震撼（Shock Wave）二選一**：旋風補近身範圍，震撼補前方射程。
2. **解除附魔（Unchanting）**：啟示錄+ 對附魔怪提供強力直接傷害，也會提高直接攻擊帶來的吸血量。
3. **暴擊（Critical Hit）**或**暈眩（Stunning）**：暴擊提高傷害與吸血，暈眩則利用高攻速長時間控住目標。

**理想鍍金附魔：**

- **虛弱（Weakening）**：命中後降低周圍敵人的傷害，穩定提高貼身生存能力。
- **暴擊／承諾（Committed）**：追求直接傷害與吸血量時使用。

旋風與震撼都很適合鬥士護手，但它們屬於**間接附魔傷害**。社群實測指出，這兩種額外傷害本身不會觸發吸血；真正提供回血的是拳頭的直接傷害。可對照 [Minecraft Wiki 的鬥士護手附魔分析](https://minecraft.wiki/w/Dungeons:Fighter%27s_Bindings/Strategy) 與 [Swirling／Shock Wave 吸血測試討論](https://www.reddit.com/r/MinecraftDungeons/comments/yj9v3h/does_swirling_and_shockwave_prevent_life_steal/)。因此本配置只保留其中一個，把其他欄位交給直接增傷或控場。

### 法器

**標準版：**

1. **煙火之箭（Fireworks Arrow）**
2. **毒帽菇（Death Cap Mushroom）**
3. **弱化之鑼（Gong of Weakening）**

適合遠古生物、Boss 與高難度關卡。弱化之鑼能讓七格內敵人受到兩倍傷害，並降低其輸出；資料見 [Minecraft Wiki：Gong of Weakening](https://minecraft.wiki/w/Dungeons:Gong_of_Weakening)。

**連發煙火優先版：**

1. **煙火之箭**
2. **煙火之箭**
3. **毒帽菇**

兩個煙火法器各自有冷卻，可輪流裝填；搭配雙冷卻盔甲，比單煙火＋弱化之鑼更貼近「連發火箭」的第一優先需求。

## 吸血究竟涵蓋哪些傷害

凋零盔甲的吸血量以造成的傷害為基礎，不是固定回復最大生命，也不是從敵人的生命上限抽取。近戰拳擊、一般遠程傷害與煙火爆炸都能提供大量回復；[Game8 的光環機制測試](https://game8.co/games/Minecraft-Dungeons/archives/289239) 也明確以煙火之箭作為快速吸血的例子。

但不能把它描述成「所有傷害都必定回血」：

- **會回血：** 鬥士護手直接拳擊、豎琴弩直接射擊、煙火之箭爆炸等可歸屬於玩家的適用傷害。
- **不計入拳擊吸血的額外傷害：** 旋風、震撼等間接附魔傷害。拳頭本身仍照常吸血。
- **不代表無敵：** 高難度爆發傷害仍可能在吸血發生前擊倒玩家，因此藥水護盾或偏轉仍有價值。

## 操作循環

1. 進場前開毒帽菇，提高近戰攻速與移動速度。
2. 遠距離先啟動煙火之箭，再用豎琴弩齊射；無盡若觸發，可立即再射同一枚特殊箭。
3. 裝有兩個煙火之箭時輪流啟動，不要同時按下，以免浪費兩次裝填。
4. 危險精英或 Boss 戰改用標準版：先敲弱化之鑼，再發射煙火，最後貼身用鬥士護手收尾。
5. 法器全部冷卻時，以遠程普通箭拉怪，或利用鬥士護手的暈眩／虛弱安全等待下一輪。

## 普通裝備與法器取得地點

以下都是關卡掉落池，**不是通關必掉**；獨特裝備可能需要反覆刷基礎類型的掉落池。

### 凋零盔甲

- 本體：仙人掌峽谷（每日試煉）、沙漠神殿、地下神殿、黑曜之巔、高塔
- DLC：靈魂沙谷（啟示錄）、破碎堡壘
- 核實：[Minecraft Wiki：Wither Armor／Obtaining](https://minecraft.wiki/w/Dungeons:Wither_Armor#Obtaining)

**凋零盔甲不在「???／蘑菇島」的一般掉落池。** 蘑菇島會掉落的是其他裝備，例如爆炸弩系；把它列為凋零盔甲高效率產地是錯誤資訊。

### 豎琴弩

- 本體：潮濕沼澤、高墩大廳、高塔
- DLC：孤獨堡壘、靈魂沙谷、要塞
- 核實：[Minecraft Wiki：Harp Crossbow／Obtaining](https://minecraft.wiki/w/Dungeons:Harp_Crossbow#Obtaining)

### 鬥士護手

- 本體：潮濕洞穴（冒險）、仙人掌峽谷（冒險）、高塔
- DLC：潮濕叢林（冒險）、珊瑚高地、要塞（啟示錄）
- 核實：[Minecraft Wiki：Fighter's Bindings／Obtaining](https://minecraft.wiki/w/Dungeons:Fighter%27s_Bindings#Obtaining)

潮濕洞穴流程短，而且解謎後有黑曜石寶箱，仍是刷護手系最方便的常規路線之一。

### 煙火之箭

- 本體：魷魚海岸、紅石礦場、高墩大廳、地下大廳
- DLC：巨型壁壘
- 核實：[Minecraft Wiki：Fireworks Arrow／Obtaining](https://minecraft.wiki/w/Dungeons:Fireworks_Arrow#Obtaining)

**苦力怕森林與南瓜牧場不在煙火之箭的標準掉落清單。** 高墩大廳則能同時刷豎琴弩、煙火之箭與毒帽菇，是這套 Build 最有效率的綜合關卡。

### 毒帽菇

- 本體：苦力怕森林、高墩大廳
- DLC：狂風山峰、扭曲森林、末地荒野
- 核實：[Minecraft Wiki：Death Cap Mushroom／Obtaining](https://minecraft.wiki/w/Dungeons:Death_Cap_Mushroom#Obtaining)

**潮濕沼澤不在毒帽菇的標準掉落清單。** 毒帽菇提供 +100% 攻速及 +20% 移速，持續時間隨力量提高；冷卻固定為 30 秒。

### 弱化之鑼

- 本體：沙漠神殿（啟示錄）
- DLC：深淵紀念碑（冒險）
- 核實：[Minecraft Wiki：Gong of Weakening／Obtaining](https://minecraft.wiki/w/Dungeons:Gong_of_Weakening#Obtaining)

## 鍍金版本：正確遠古生物與符文

遠古狩獵的符文是「讓指定遠古生物有機會生成」的最低組合，並不保證每次地圖都出現；投入附魔點數可提高遠古生物房間的生成機率。

### 凋零盔甲

- 目標遠古生物：**Grim Guardian**
- 需求符文：**I + I + A**
- 掉落池包含冷酷盔甲系，因此可能掉落鍍金凋零盔甲。
- 核實：[Grim Guardian Ancient Dungeon](https://minecraft.wiki/w/Dungeons:Grim_Guardian_Ancient_Dungeon)、[Wither Armor 的 Ancients 欄](https://minecraft.wiki/w/Dungeons:Wither_Armor#Ancients)

### 豎琴弩

- 目標遠古生物：**Pestilent Conjurer**
- 需求符文：**C + R + I**
- 掉落池包含散射弩系，因此可能掉落鍍金豎琴弩。
- 核實：[Pestilent Conjurer Ancient Dungeon](https://minecraft.wiki/w/Dungeons:Pestilent_Conjurer_Ancient_Dungeon)、[Harp Crossbow 的 Ancients 欄](https://minecraft.wiki/w/Dungeons:Harp_Crossbow#Ancients)

### 鬥士護手

- 目標遠古生物：**?????（遠古蘑菇牛）**
- 需求符文：**C + I + P + A**
- 掉落池包含護手系，因此可能掉落鍍金鬥士護手。
- 核實：[????? Ancient Dungeon](https://minecraft.wiki/w/Dungeons:%3F%3F%3F%3F%3F_Ancient_Dungeon)、[Fighter's Bindings 的 Ancients 欄](https://minecraft.wiki/w/Dungeons:Fighter%27s_Bindings#Ancients)

## 最順暢的成形路線

1. **苦力怕森林：** 先拿毒帽菇；煙火之箭不在這關，不能期待一起掉落。
2. **潮濕洞穴：** 刷取鬥士護手，先用旋風或震撼版本過渡。
3. **沙漠神殿／地下神殿／黑曜之巔：** 刷取凋零盔甲，建立近遠程通用吸血。
4. **高墩大廳：** 集中刷豎琴弩、煙火之箭與更高力量的毒帽菇；這才是三項核心零件重疊最多的關卡。
5. **遠古狩獵：** 分別鎖定 Grim Guardian、Pestilent Conjurer 與 ?????，追求正確的鍍金第四附魔。

## 常見錯誤與核實結論

- **「凋零盔甲去蘑菇島刷」：錯。** 正確一般掉落池見 [Wither Armor](https://minecraft.wiki/w/Dungeons:Wither_Armor#Obtaining)。
- **「煙火之箭掉落於苦力怕森林、南瓜牧場」：錯。** 正確清單見 [Fireworks Arrow](https://minecraft.wiki/w/Dungeons:Fireworks_Arrow#Obtaining)。
- **「毒帽菇掉落於潮濕沼澤」：錯。** 正確清單見 [Death Cap Mushroom](https://minecraft.wiki/w/Dungeons:Death_Cap_Mushroom#Obtaining)。
- **「連鎖反應會產生次級小火箭」：描述不精確。** 附魔本身定義為命中後產生五枚額外箭矢，見 [Chain Reaction](https://minecraft.wiki/w/Dungeons:Chain_Reaction)。
- **「無盡等於永久連發煙火」：錯。** III 級只有 48% 免耗機率，見 [Infinity](https://minecraft.wiki/w/Dungeons:Infinity)。
- **「虛空打擊是豎琴弩最佳鍍金」：不建議。** 同武器再次命中會重設倍率，見 [Void Strike](https://minecraft.wiki/w/Dungeons:Void_Strike)。
- **「旋風與震撼傷害也會吸血」：社群實測不支持。** 兩者屬間接傷害；參考 [實測討論](https://www.reddit.com/r/MinecraftDungeons/comments/yj9v3h/does_swirling_and_shockwave_prevent_life_steal/)。
- **「鬥士護手固定每秒 7.14 拳」：缺乏版本條件。** 武器曾在 1.16.2.0 調整攻擊間隔，見 [Fighter's Bindings 歷史](https://minecraft.wiki/w/Dungeons:Fighter%27s_Bindings#History)。
- **「三件鍍金裝備的遠古生物與符文」：原組合皆不正確。** 正確組合分別為 IIA、CRI、CIPA，來源見上一節三個 Ancient Dungeon 條目。

## 最終結論

這套 Build 適合把「煙火連射」放第一順位、又不願犧牲近遠程通用回血與高速拳擊的玩家。真正的畢業重點不是只追求四個漂亮附魔，而是：

1. 用**雙冷卻凋零盔甲**縮短兩個煙火法器的空窗。
2. 用**無盡＋多重射擊＋連鎖反應豎琴弩**放大每次煙火裝填。
3. 讓鬥士護手至少保留兩格直接增傷／控場，避免旋風與震撼同時佔滿、卻無法提高吸血量。
4. 用正確遠古生物與符文定向刷鍍金裝備，不要依錯誤掉落表浪費獻祭品。

延伸閱讀：[裝備與法器完整圖鑑](/post/gaming/minecraft-dungeons-equipment-catalog/)｜[大量複製一般箭矢與 50+ 煙火箭（版本限定技巧）](/post/gaming/minecraft-dungeons-infinite-arrow-bug-guide/)｜[遠古狩獵四套 Build 與獻祭組合](/post/gaming/minecraft-dungeons-ancient-hunt-strategy/)
