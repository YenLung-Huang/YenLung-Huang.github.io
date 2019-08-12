---
title: 在 Windows 上面安裝 Valet
date: 2019-07-20 21:43:41
tags:
- php
- laravel
- valet
- windows
- chocolatey
---
## 前言
過去使用 Homestead 開發 Laravel 專案總是驚嘆 Laravel 社群提供的自動化開發環境建置非常的強大，讓 php 開發人員不太需要花很多的時間去學習，不過冗長的啟動過程，有時候只是想快速的測試一些新的東西時，都會感覺一種很窒息的感覺，覺得很笨重，只是想快速了解一些語法開發方式，結果，整個vagrant up 的部署過程，讓人覺得像是揹著老太太走路，又臭又長。
這時候想到 Laravel 官網有介紹到 Valet 基於 mac 的開發

## 事前準備工作

### 以 chocolatey 安裝
windows 的巧克力(套件管理工具)，像是 Ubuntu 的 apt 及 Mac 的 brew，讓習慣用指令安裝的人，有一種吃巧克力的幸福感，可以省去滑鼠左鍵瘋狂點擊下一步
[https://chocolatey.org](https://chocolatey.org/)

* 安裝 chocolatey 非常簡單，以 管理員身分執行 powershell，執行以下指令安裝 chocolatey

```powershell
Set-ExecutionPolicy Bypass -Scope Process -Force; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))
```

chocolatey 安裝完成後，檢查是否安裝完成
```powershell
# 檢查是否安裝完成
choco -v
```
確認安裝完成之後，開始安裝基本環境

* 首先安裝 php、mysql

```powershell
# 安裝 php
choco install php -y
# 安裝 mysql
choco install mysql -y
```

確認php 環境安裝完成之後，安裝composer，前往[composer](https://getcomposer.org/download/)下載頁面下載.exe執行檔安裝

```powershell
# 檢查 php 是否安裝
php -v
# 檢查 mysql 是否安裝
mysql -v
```
## 安裝 Valet

Windows 安裝
```powershell
composer global require cretueusebiu/valet-windows
```
Windows：用管理员身份运行以下命令
```
valet install
```

Windows 10 用戶必須手動調整 DNS 服務器，在網卡的IPv4和IPv6設置裡，分別填入127.0.0.1和:: 1作為DNS服務器地址。
[參考網址](http://mayakron.altervista.org/wikibase/show.php?id=AcrylicWindows10Configuration)

## 配置 Valet
一切準備就緒之後，將目錄切換到project底下
```
# 切換到先對應的目錄底下
cd project
# 建立 index.html
echo 'hello world' >> index.html
# 建立連結
valet link project
```

## 參考資源
[https://kazumi.blog/how-to-use-valet-to-build-laravel-testing-env-easily-cn.html](https://kazumi.blog/how-to-use-valet-to-build-laravel-testing-env-easily-cn.html)
