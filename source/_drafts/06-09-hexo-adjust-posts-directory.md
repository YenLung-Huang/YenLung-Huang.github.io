---
title: 調整 Hexo 的目錄文章
date: 2020-06-09 22:58:24
categories:
 - hexo
tags:
 - hexo
---


# 目錄調整

hexo默认的文章全部存在\source\_posts\一个文件夹下面，文章一多就不方便管理。
所以对_posts目录里的文章按日期进行适当的整理。尝试了一下，找到了比较满意的做法。

# 預設值
打開 _config.yml 搜尋 new_post_name
```
# Writing
new_post_name: :title.md # File name of new posts

```

可以看到他預設的格式為 :title.md 他這個意思代表

文章的默认地址为：域名/年/月/日/标题（文件名）
例：我现在hexo new post 001会在\source\_posts\生成一个001.md文件，该文章的链接为：https://waitung.cc/2018/06/18/001/
所以如果我：
2017年11月16日写下开始用hexo写文章
2018年02月25日写下去XX旅游
2018年05月03日写下常用工具整理
默认设置下：
hexo new post 开始用hexo写文章
hexo new post 去XX旅游
hexo new post 常用工具整理
文件：
source
　　└_post
　　　　├开始用hexo写文章.md
　　　　├去XX旅游.md
　　　　└常用工具整理.md

这样文章一多的时候_posts目录就会显得非常乱。
做法一：直接整理文章名字，只改动title: 文章标题。
hexo new post 001
hexo new post 002
hexo new post 003
文件：
source
　　└_post
　　　　├001.md
　　　　├002.md
　　　　└003.md

# 解決方法為 在_post目录里再建立多一级的目录。
修改为：new_post_name: :year/:month-:day-:title.md

hexo new post 开始用hexo写文章
hexo new post 去XX旅游
hexo new post 常用工具整理
文件：
source
　　└_post
　　　　├2017
　　　　│　└01-16-开始用hexo写文章.md
　　　　└2018
　　　　　　├02-25-去XX旅游.md
　　　　　　└05-03-常用工具整理.md
地址：
https://waitung.cc/2017/11/16/开始用hexo写文章/
https://waitung.cc/2018/02/25/-去XX旅游/
https://waitung.cc/2018/05/03/常用工具整理/

在方法三的基础再以年份把文章分开文件夹存放。
按不同需要还可以修改new_post_name达到不同效果。
例：
hexo new post post001

new_post_name: :year/:month/:title.md
\source\_post\2018\06\post001.md
new_post_name: :year-:month/:day-:title.md
\source\_post\2018-06\post001.md
还可以:

new_post_name: :year/:month/:year-:month-:day-:title.md
\source\_post\2018\06\018-06-18-post001.md
方便搜索用。

(參考來源)[https://blog.waitung.cn/2018/06/18/hexo-arrange.html]