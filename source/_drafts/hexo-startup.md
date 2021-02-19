---
title: hexo blog
date: 2019-08-11 21:49:24
tags:
- hexo
- blog
- seo
---
https://zhuanlan.zhihu.com/p/35668237
## Hexo startup
因為希望有一個空間可以整理歸納自己的一些所學的東西，所以便開始找尋適合作為 Blog 的工具，
之前使用過 Wordpress 一段時間，但發現了 Hexo 更方便，所以這邊來紀錄一下使用過程。
[https://hexo.io](https://hexo.io)

## Hexo 優點
How to use Hexo and deploy to GitHub Pages
https://github.com/hexojs/hexo
https://hexo.io/docs/
1. Install Hexo
```
$ sudo npm install -g hexo-cli

$ hexo -v
hexo-cli: 0.1.9
os: Darwin 14.3.0 darwin x64
http_parser: 2.3
node: 0.12.7
v8: 3.28.71.19
uv: 1.6.1
zlib: 1.2.8
modules: 14
openssl: 1.0.1p
```
2. Create a project for your GitHub Pages
```
$ hexo init yt8yt.github.io
INFO  Copying data to ~/***/yt8yt.github.io
INFO  You are almost done! Don't forget to run 'npm install' before you start blogging with Hexo!

$ cd yt8yt.github.io

$ npm install
```
3. Run a test server for your page on Mac
```
$ hexo server
INFO  Hexo is running at http://0.0.0.0:4000/. Press Ctrl+C to stop.
```
4. Set information for your new blog

https://hexo.io/docs/configuration.html

$ vi _config.yml

~~~~~~~~~~~~~~~~~~ _config.yml ~~~~~~~~~~~~~~~~~~
# Site
title: yt8yt's note
subtitle:
description: yt8yt's personal blog
author: yt8yt
language:
timezone: Japan

# URL
## If your site is put in a subdirectory, set url as 'http://yoursite.com/child' and root as '/child/'
url: http://yt8yt.github.io/
root: /
permalink: :year/:month/:day/:title/
permalink_defaults:
5. Set information to use Git
https://github.com/hexojs/hexo-deployer-git

$ npm install hexo-deployer-git --save
$ vi _config.yml

~~~~~~~~~~~~~~~~~~ _config.yml ~~~~~~~~~~~~~~~~~~
# Deployment
## Docs: http://hexo.io/docs/deployment.html
deploy:
  type: git
  repo: git@github.com:yt8yt/yt8yt.github.io.git
  branch: master
6. Set "watch" before starting your work
"watch" command can monitor your files.
https://hexo.io/docs/generating.html

$ hexo generate --watch
7. Create a new post file
$ hexo new first-post
INFO  Created: ~/***/yt8yt.github.io/source/_posts/first-post.md
8. Edit the above file with Markdown or Hexo's Helper
Hexo's Helper
https://hexo.io/docs/helpers.html
I use Atom with "shift + control + m" when I use Markdown :-)
https://atom.io/

9. Delete "source/_posts/hello-world.md"
It's not necessary to deploy.

10. Deploy your new blog!!
https://hexo.io/docs/deployment.html

$ hexo clean
$ hexo deploy
After writting the above command, you can see your new blog on GitHub Pages.
http://******.github.io/

11. Change your blog theme
https://github.com/hexojs/hexo/wiki/Themes

For instance, How to use the following theme.
https://hexo.io/hexo-theme-light/

## Install it
$ cd yt8yt.github.io
$ git clone git://github.com/tommy351/hexo-theme-light.git themes/light

## Update the above files
$ themes/light
$ git pull

## Set information to use the theme
$ cd yt8yt.github.io
$ vi _config.yml

~~~~~~~~~~~~~~~~~~ _config.yml ~~~~~~~~~~~~~~~~~~
# Extensions
## Plugins: http://hexo.io/plugins/
## Themes: http://hexo.io/themes/
theme: light
12. Create a new page file
https://hexo.io/docs/writing.html

$ hexo new page aboutme
INFO  Created: ~/***/yt8yt.github.io/source/aboutme/index.md

$ cd source/aboutme/

$ vi index.md
13. Use "Read More"
Write <!-- more --> in your articles.

14. Use Plugins
https://github.com/hexojs/hexo/wiki/Plugins
前言
前一篇 建立使用量分析的網頁 中所寫到最後的解決方法是使用 Hexo + GitHub pages 所建立的 Blog 來加上 Google analytics，而這篇就要來教大家如何使用 Hexo 來產生靜態網頁，並加上GitPage 自動更新部署。
完全無須考慮 HTML、CSS、伺服器、資料庫等這些發布網站的必備技能。
環境配置
安裝 Node.js
安裝 Git
安裝 Hexo
上述兩個安裝完之後，接著執行下方指令即可安裝Hexo。
$ npm install -g hexo-cli
使用 Hexo
安裝完Hexo 後，執行下方指令，Hexo 就會在指定資料夾 <folder> 中新建所需要的的檔案。記得將 <folder> 替換名稱喔～
$ hexo init <folder>
$ cd <folder>
$ npm install
完成後，基本的檔案結構長這樣～

_config.yml：網站 配置 檔案，可以在此配置大部分的設定。
package.json：套件版本控制
scaffolds：鷹架 資料夾。建立新文章時，會根據 scaffold 來建立檔案。
source：原始檔案資料夾是放置內容的地方。
themes：主題 資料夾。Hexo 會根據主題來產生靜態檔案。
常用指令
接著執行下方兩行指令，就可以在 http://localhost:4000/ 查看Blog 。
$ hexo g
$ hexo s

噹啷～～Blog 的雛型已經出來了～～
hexo generate (hexo g) 產生靜態檔案，會在目錄下產生public 資料夾。
hexo server (hexo s) 啟動伺服器，預設是 http://localhost:4000/。
hexo deploy (hexo d) 部署網站。（ 比如 github, heroku 等平台 ）
發佈文章
$ hexo new [layout] <title>
如果沒有設定 layout 的話，則會使用 _config.yml 中的 default_layout 設定代替。如果標題包含空格的話，請使用引號括起來。
所以在使用上可以解釋成：
$ hexo new “postName” # 新建文章
$ hexo new page “pageName” # 新建頁面
所有的文章都會在source/_posts裡面。一開始裡面就已經有一篇範例文章hello-world.md了。
常用组合
$ hexo d -g # 產生靜態檔後部署
$ hexo s -g # 產生靜態檔後預覽
更換主題
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

在 GitHub 上新增 GitHub Pages
走到這裡，只剩下最後一步了！就是讓大家都能看到你的部落格！
部署的方式有很多種，而這次就使用最簡單的 Github Page。
在GitHub 創建一個名稱為<username>.github.io 的專案
2. 安装 deploy git 插件
npm install hexo-deployer-git --save
3. 在主題配置文件 _config.yml 中修改 repository 名稱
deploy:
  type: git
  repo:
    github: git@github.com:<username>/<username>.github.io.git
4. 執行 hexo d 即可發佈到 GitHub 上
噹啷～～接下來就可以到你的網站<username>.github.io來看看囉～～