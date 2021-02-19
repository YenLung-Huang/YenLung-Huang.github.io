---
title: Vim or Neovim php developer settings
date: 2019-08-11 21:49:24
tags:
- vim
- neovim
- php
---

## Hexo startup
因為希望有一個空間可以整理歸納自己的一些所學的東西，所以便開始找尋適合作為 Blog 的工具，
之前使用過 Wordpress 一段時間，但發現了 Hexo 更方便，所以這邊來紀錄一下使用過程。

## Hexo 優點
因為建立於本地端，所以可以更方便離線進行編輯
可以不需要一台伺服器
文章編輯使用 Markdown 語法，更方便、通用、容易上手
部署於 GitHub 上，完全零成本
中文兼容性高
可快速搭建優質的部落格
開始之前
建議先了解，cmd 或是 bash 指令
之後所有指令以 ‘$’ 開頭，皆為 bash 指令
​
有任何問題，都歡迎留言詢問唷～

建制步驟
安裝 Node.js
去 Node.js 官網下載安裝

安裝 Hexo Git
$ npm install hexo-deployer-git --save
安裝 Hexo
使用 npm 來安裝 hexo (須先安裝 Node.js)

$ npm install hexo-cli -g
安裝成功後，輸入以下指令可查看版本

$ hexo version
接下來即可初始化我們的部落格了

$ hexo init blog       # 初始化 blog
$ cd blog              # 移動到剛創建的 blog 資料夾裡
$ npm install       # 安裝相關套件
將 Hexo 配置到 GitHub
去 GitHub 官網登入。
新增一個倉庫(Repositories)



倉庫名稱為 yourname.github.io

上面的 yourname 請替換成你 GitHub 的帳號名稱



看到這頁代表即可退出



再來到 blog 資料夾下找一個 _config.yml 的檔案，這是 Hexo 的全域配置文件


開啟之後，拉到檔案最底部，可以看到

deploy:
  type:
將以下資訊對應輸入

deploy:
  type: git
  repository: http://github.com/yourname/yourname.github.io.git
  branch: master
設定中的 “:” 後一定要有一個空格
將上面的 yourname 改成妳的 GitHub 帳號名稱

產生靜態文件後，部署上 GitHub

$ hexo d -g
再來就可以上 https://yourname.github.io/ 查看是否部署成功
成功之後，就可以開始做一些優化和寫文章啦。

將上面的 yourname 替換成你 GitHub 的帳號名稱

Hexo 配置檔介紹
_config.yml 是 hexo 的預設設定黨，其設定是用 yaml 格式編寫。

yaml 檔裡，”:”後一定要有一個空格
下面是 hexo 的預設配置，可以自修改。

# Site
title: /標題(會顯示在網頁標題與頁首)/
subtitle: /子標題(顯示在頁首)/
description: /內容描述(給搜尋引擎看的)/
author: /作者(顯示在頁尾)/
language: /網站預設語言(台灣:zh-tw)/
timezone: /時區(預設使用你電腦的時區)/

# URL
url: /網站的網域位址/
root: /網站根目錄/
permalink: /文章目錄(預設使用 YYYY\MM\DD\文章名稱)/

# Extensions
theme: /網站的佈景主題/
       (可以到"https://hexo.io/themes/"下載喜歡的佈景放置到 theme 目錄裡)

# Deployment
deploy:
    type: /發佈型態/ 例如(git、heroku、rsync、openshift、ftpsync)
    repository: /部署位置/ 例如(git@github.com:帳號/REPO名.git)
    branch: /分支/ 例如(master、gh-pages)
    message: /部署訊息/
使用 Next 主題
本站使用主題為 Next.Pisces 主題。
如何使用，可以參考 官方教學文件，上面寫的很詳細，而且是中文的教學！

發布文章
創建文章

$ hexo new [postName]
備註：將 [postName] 換成你的文章名稱 (以英文尤佳)

前往 source / _post 資料夾中，打開 [postName].md 文件，在最下面新增 Markdown 語法的內容。

修改完後，執行以下指令，就可以將新的變更發佈到部落格上囉！

$ hexo d -g    # d = 部署, g = 生成
等一段時間，就可以看到你剛剛打的文章囉！

如果你要先在本地端看看效果，也可以改成以下指令

$ hexo server
不熟悉 Markdown 的人，可以去看看這篇 Markdown 語法教學

如果想嘗試編寫 Markdown，或是想找一個好用的Markdown 編輯器，可以嘗試使用 HackMD。

刪除文章
首先進入到 source / _post 資料夾中，找到 helloworld.md 文件，在本地直接執行刪除。


執行以下指令

$ hexo clean    # 清除快取檔案和已產生的靜態檔案。
$ hexo d -g     # d = deploy, g = generate
等一段時間，就會發現那篇文章已經消失囉！

使用第三方擴充服務
本站有使用以下第三方服務，有興趣可以去看看。

DISQUS：評論系統
Local Search：搜尋系統
文章摘要顯示使用：優化主頁文章摘要
不蒜子统计：瀏覽量統計
客製化設定
本站參考了以下幾篇文章，修改了一些顯示效果，有興趣可以看看。

讓NexT主題的Markdown H2自動產生底線
讓NexT主題的List不只有圓形
修改文章底部的那个带#号的标签
動態背景
登錄搜尋引擎
如果只支援 Google 可以參考這篇 Next+Google Webmaster tools，
如果也想支援百度，可以參考這篇 Hexo+Next主题博客提交百度谷歌收录。

GitHub 會擋百度爬蟲。如果你建在 GitHub 上，百度會搜尋不到
要避免讓 GitHub 網站被百度擋，有一個解法，可以參考看看
使用coding.me加速Hexo博客访问

SEO 優化
可以參考這篇，基于Hexo中Next主题的SEO优化指南。

強化 Markdown renderer
執行以下指令，將原生 Markdown 改為 Markdown-it

$ npm un hexo-renderer-marked --save    # 刪除原生 Markdown
$ npm i hexo-renderer-markdown-it --save    # 安裝 Markdown-it
新增標籤頁
可以參考 Next 官網的這篇教學 添加「标签」页面。

新增分類頁
可以參考 Next 官網的這篇教學 添加「分类」页面。

新增關於頁
可以參考 Next 官網的這篇教學 Hexo about页面怎么写 Next关于页面怎么设置。

性能優化
可以參考這兩篇，分別用不同的方法將靜態資源進行壓縮

Hexo博客-Next性能优化之路
hexo博客加速之页面压缩
文章編輯後台
如果覺得編輯完無法立即看到結果，或是結果和本地編輯器有差，可以試著使用看看 hexo-admin，hexo-admin 博客后端管理工具

使用文章編輯後台一個禮拜後的結論：難用，不建議使用！
建議可以在自己熟悉的 markdown 編輯器編輯就好。

參考資料
Hexo部落格建立筆記 | SkyLake’s Blog
Hexo 官方網站
Next 官方網站