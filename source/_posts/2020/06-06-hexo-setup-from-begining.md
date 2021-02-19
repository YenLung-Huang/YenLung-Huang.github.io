---
title: Hexo setup from begining
date: 2019-06-06 00:00:31
updated: 2020-06-07 00:00:34
categories:
- hexo
tags:
- windows
- hexo
---

# 前言:
隨著經歷的事情越來越多，漸漸地發現要把腦袋中的一些東西，交由外部的工具來幫忙管理，因為人也年長了，不像是年輕的時候需要做的事情比較簡單單純，步入社會後，繁雜的事物全部都印入腦袋，碎片化的資訊，讓一件事情不再是那麼有條理，畢竟，人的腦袋的容量是有限的，善用工具才能幫助自己更快速的學習消化儲存知識。至於，blog 為什麼要選擇 hexo，就只是單純的，想要一個很簡單，很快速能記錄整理自己想法的地方，hexo 就是一個能快速達成目標的工具，hexo 的生態也不錯，該有的外掛都不少於 wordpress，以文章來說足夠了。

<!-- more -->

# 需求:
 - [npm](https://nodejs.org/en/download/) 
 - [git](https://git-scm.com/)
 - [hexo](https://hexo.io/)
 - 任一編輯軟體

# 著手進行
官方文檔上面已經有不錯的建立步驟，不過這篇文章還是希望能幫助自己整理一下 hexo 有的功能

## 安裝 hexo 指令
```shell
npm install hexo-cli -g

```

切到你想要的目錄后，初始化博客的環境只需要以下幾行指令（假設創建的資料夾叫做blog）
## 建立 blog 及 預覽畫面
```shell
cd ${blog_directory}
hexo init blog
npm install
hexo server
```
用瀏覽器打開[http://localhost:4000](http://localhost:4000)

## blog 結構
在 hexo 的目錄底下

```
.
├── _config.yml
├── package.json
├── scaffolds
├── source
|   ├── _drafts
|   └── _posts
└── themes
```

_config.yml：網站 配置 檔案，可以在此配置大部分的設定。
package.json：套件版本控制
scaffolds：鷹架 資料夾。建立新文章時，會根據 scaffold 來建立檔案。
source：原始檔案資料夾是放置內容的地方。
themes：主題 資料夾。Hexo 會根據主題來產生靜態檔案。


# 開始寫文章

開始使用 hexo 寫 blog，只需要以下三個指令就能完成

## 發布文章

使用這個指令產生的文章會放在 _posts 目錄底下，放在這邊的文章會直接發佈出去

```shell
hexo new <title>
```

## 草稿

使用這個指令產生的文章會放在 _drafts 目錄底下，放在這邊的文章需要使用 publish 或者手動移到 _post 底下才會發佈出去

```shell
hexo new draft <title>
```

## 發布草稿

用來將放在 _drafts 目錄底下的草稿發佈
```shell
hexo publish <title>
```


# 完成

基本上使用及預覽 hexo 就完成了。