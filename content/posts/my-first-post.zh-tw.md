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

當專案建立完成後，第一件事就是挑選主題。到 [Hugo 的主題列表](https://themes.gohugo.io/) 挑選一個符合情境需求的主題。

以這個部落格為例，我選的是 [DoIt](https://themes.gohugo.io/themes/doit/) 主題。在列表中找到 DoIt 並點進去後如下圖：

![power-shell](/images/hugo-tutorial-1/themes-banner.png "主題 DoIt 頁面")

在挑的時候可以先看看線上 Demo 狀況如何，以及下方會描述這個主題的內容，可以多看看進行篩選。

選好主題後，有兩種方式可以進行安裝：

- 直接下載包
- git submodule download
### 直接下載

直接下載[github](https://github.com/HEIGE-PCloud/DoIt.git)上的原始碼壓縮檔，解壓縮至 `themes/DoIt` 資料夾。

### Git submodule download

```shell
git submodule add https://github.com/HEIGE-PCloud/DoIt.git themes/DoIt
```

其實都是在做同一件事情，就是把主題的原始碼放進`themes`的資料夾內。而其中差別在於；直接下載的話，我們並不能追蹤主題的更新。如果用Github submodule的話，則可以保持主題在最新狀態。

### 啟動主題

打開位於專案目錄底下的`config.toml`，如下圖：

![config.toml](/images/hugo-tutorial-1/config.toml.png "基本設定")

加上主題參數的設定：

```env
# 主題設定為 DoIt 主題
theme = "DoIt"
```

這樣主題就設定完成了！

## 建立文章

設定玩主題後，我們可以開始為自己的部落格開始添加內容啦。首先，我們可以用下列的命令新增第一篇文章：

```shell
hugo new posts/my-first-post.md
```

指令完成後，注意`content/posts`資料夾，會出現剛剛指令所新增的檔案：`my-first-post.md`。內容如下：

```markdown
---
title: "My First Post"
date: 2019-03-26T08:47:11+01:00
draft: true
---
```

- `title` 屬性代表的是這篇文章的標題

- `date` 屬性為建立時間

- `draft` 屬性確認是否為手稿

相關設定我們可以先不用理他，直接在設定的底下開始寫文章。

```markdown
---
title: "My First Post"
date: 2019-03-26T08:47:11+01:00
draft: true
---

# 哈囉這是我第一篇文章

內容內容。
```

寫文章時採用的是 markdown 語法，具體用法可以參閱[這裡](https://markdown.tw/)。

將剛剛編輯好的內容儲存，就完成文章的新增啦！。

## 啟動本地服務

現在，我們已經萬事具備了。只要將本地的服務啟動，就可以看到我們剛剛所建立的部落格。而只要執行下列指令：

```shell
hugo server -D
```

沒錯，就這麼簡單，終端機會將網站的網址列印在畫面上，以我的電腦為例是`http://localhost:8000`。複製網址，打開Chrome瀏覽器，貼上網址就可以看到網站啦！是不是非常容易呢。