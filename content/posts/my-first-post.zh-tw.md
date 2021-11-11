---
title: "從0到100，自己架設部落格！"
date: 2021-11-10T17:24:22+08:00
author: "Simen"
keywords: "關鍵字"
---

# 前言

為什麼會想開始寫部落格呢？自從開始發現自己上了年紀，東西丟三落四之後。就想好好找個地方，把東西存起來，等到需要用的時候再回來翻。

期間找過各種筆記軟體，如Notion、HackMD等等。在Survey的期間，不免又在想，我需要紀錄的東西，能幫助到某些有緣人也不一定。所以產生了自己架部落格的想法。於是就有了這個部落格啦。

本篇將會手把手教你如何快速地安裝以及使用 **Hugo**！

## 前置作業

在開始之前，我做了許多功課。先談談線上的服務。我試過下面幾個服務：

- HackMD
- Notion (本身還在使用)
- Medium

<!-- Gastby.js Vue -->

### 靜態頁面生產器

### 選擇 HUGO 的理由。

看來看去，因為自己本身也想學GO，一看到這個專案 Github 星星數又多，二話不說就入坑啦。

# 安裝Hugo

## 開始安裝

安裝 **HUGO** 相當的簡單，根據官方文件，我們只需要依序執行指令，就能完成hugo的安裝。

## 如果你是 Windows 用戶：

如果你使用 windows ，你需要裝**套件管理器**來完成 **Hugo** 的安裝。為了完成接下來的步驟，我們必須先把Power shell開啟，並以管理員身分執行。

以下的指令區塊都是在 Power shell完成。

![power-shell](/images/hugo-tutorial-1/power-shell.png "搜尋Power Shell，以管理員身分執行")

官方提供以下兩個套件作為範例：

### 使用 Chocolatey

安裝[Chocolatey](https://chocolatey.org/)(參考官網資訊，下方複製指令便可以安裝，貼進Power shell執行即可)後，輸入以下指令：

```shell
choco install hugo -confirm
```

接著等待安裝過程，就完成了。測試看看有沒有安裝成功：


```shell
hugo version
```

結果如下圖，出現版本號代表安裝成功！

![power-shell](/images/hugo-tutorial-1/hugo-help.png "搜尋Power Shell，以管理員身分執行")

## 建立專案

安裝好Hugo的CLI套件之後，接著就可以開始建立自己的專案。先進入要放置專案的資料夾。接著輸入建立專案的指令。

```shell
cd /your/projects/path 
hugo new site Myblog
```

下完指令後，你會發現在資料夾底下，生成了一個`Myblog`的資料夾，我們的專案就建立完成了。

建立好專案之後就可以開始進行專案設定，首先我們要做的是進入專案的路徑：

```shell
cd /your/projects/path/Myblog
```

## 加入網站主題