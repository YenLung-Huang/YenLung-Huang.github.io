---
title: Hexo choose theme
date: 2020-06-06 00:00:31
category:
- hexo
tags:
- windows
---

# Hexo themes

Hexo 上面本身已經有很多的好看的主題

# Ayer theme

每個人都有自己的喜好，不管做什麼選擇更換主題
NexT
Hexo 預設的主題是landscape，而我們可以到 這裡 來挑選我們想要的主題，而其中最多人用的應該就屬 NexT 了。
安裝NexT
$ git clone https://github.com/theme-next/hexo-theme-next.git themes/next
接著修改網站設定_config.yml
theme: next
重新啟動server
$ hexo server

噹啷～～主題也改變了～～
語言設定
在_config.yml中找到language，設定為zh-tw
language: zh-tw
這樣就可已支援繁體中文。
Scheme 設定
在NexT 中有多種Scheme 可選擇，其中的預設主題為Muse。大部份看到蠻多人選擇使用Pisces當主題。
在主題設定theme/next/_config.yml裡找到schema，把註解去掉即可開啟。
#scheme: Muse
#scheme: Mist
scheme: Pisces
#scheme: Gemini
代碼高亮
NexT 使用 Tomorrow Theme 當作代碼高亮，共有5款主題可以選擇。 NexT 預設使用的是 normal，可選的值有 normal、night、 night blue、 night bright、 night eighties
highlight_theme: normal
背景特效
在主題設定themes/next/_config.yml裡還有另外的動畫效果，要打開就把值設定為true。

而其中最多人開啟的就屬 canvas_nest 了，大家可以試試看這個驚喜呦～
開啟社群帳號連結
在主題設定themes/next/_config.yml中新增社群網路連結。