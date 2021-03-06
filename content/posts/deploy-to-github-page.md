---
title: "將部落格部署 至 Github Page"
date: 2021-11-18T15:40:26+08:00
author: "Simen"
keywords: "關鍵字"
---

## 前言

前篇 ＂[自己架設部落格](/posts/my-first-post)＂，已經能建立起我們自己的部落格網站了，但僅止於個人的電腦內。建立部落格我們當然希望讓其他人也看到，所以我們今天要將自己的部落格部署上雲端，讓大家可以瀏覽！

## 前置作業

我們需要準備的東西有以下幾個：

- 網址： 網址就像我們的地址，我們的品牌所以必備！
- 主機： 可以放置部落格的伺服器。

### 購買網址

我個人的話是習慣在 [GoDaddy](https://tw.godaddy.com/) 進行購買，所以這邊就用GoDaddy作為範例。

首先決定你想要的網域：例如`exmaple.com`,`exmaple.tw`...等。

![domain-search](/images/deploy-to-github-page/domain-search.png "搜尋你喜歡的網址")

GoDaddy 會幫你搜尋出目前可以用的網址以及相似詞，點擊喜歡的網址加入購物車。

![add-to-cart](/images/deploy-to-github-page/add-to-cart.png "將網址加入購物車")

選好網址後，點擊右上角進入購物車。

![checkout](/images/deploy-to-github-page/checkout.png "購物車 - 結帳")

接著就是一連串的結帳動作了，這邊就是乖乖付錢了事啦。

> 至於網址要買多久，如果不想一次付太多錢的話，我是一次先買一年。稍後管理自己的網域時，你可以選擇是否要自動續約，會自動從信用卡扣款。如果付款不成功，你的網址將會失效。

購買好網址之後，我們接著進行伺服器的挑選。

### 伺服器挑選

市面上可以放伺服器或網站的主機商很多，這邊要如何挑選呢？我這邊是直接選擇 [Github](https://github.com/) 的 `Page` 功能，這樣就不用額外再去付費購買主機。

#### Github Page

甚麼是 Github Page ？ 我們知道 **Github** 是讓人們上傳自己的程式碼或做版本控制上傳檔案的地方。而 **Github** 提供了一種功能，讓你能夠不用購買主機，就能把網站部署在雲端，稱之為 Github Page。 大致上就是用你上傳的檔案指定某個資料夾為伺服器的 `Host` 目錄，當輸入網址連進去的時候，用這個資料夾裡面的靜態檔案顯示網站。

#### 註冊 Github

註冊相信大家都會，照著網站上的步驟填妥資料，你就可以拿到新鮮的帳號啦。

## 開始部署

上述準備事項完成之後，就可以開始進行部署的動作了。我們需要將部落格上傳至 **Github** ，首先需要開一個 Repository (儲存庫)。

### 設定 Gitgub Page

![create-repository](/images/deploy-to-github-page/create-repository.png "建立儲存庫")

輸入名稱，就可以直接建立了。如果不清楚底下的設定，全部不勾選即可。

![create-repository-2](/images/deploy-to-github-page/create-repository-2.png "建立儲存庫 - 填寫")

建立好的 Repository 目前是完全空白的狀態。點擊上方複製按鈕，將 Repository 的位置複製起來。

![done-repo](/images/deploy-to-github-page/done-repo.png "完成建立")

接下來我們要將 Hugo的內容輸出成網頁伺服器看得懂的樣子。首先開啟 **Power Shell** ，並進入你的部落格專案資料夾。

![cd-to-your-home](/images/deploy-to-github-page/cd-to-your-home.png "進入專案資料夾")

將部落格內容打包成 `HTML檔案` ，只需要跑以下的指令：

```shell
// 執行打包命令
hugo

// 以下是輸出
Start building sites …
hugo v0.89.2-63E3A5EB windows/amd64 BuildDate=2021-11-08T15:22:24Z VendorInfo=gohugoio

                   | ZH-TW
-------------------+--------
  Pages            |    11
  Paginator pages  |     0
  
...
```

對，就這麼簡單。接著你會看到專案底下長出一個資料夾 `public` ，裡面的內容就是打包好的 `HTML檔案`。

![html-packed](/images/deploy-to-github-page/html-packed.png "打包成功!")

接著一樣使用 Power shell，`CD` 進入 public 資料夾，執行以下指令：

```shell
    git init // 初始化 git
    git branch -M main // 開啟主要分支
    git add -A // 將所有檔案加入追蹤
    git commit -m "init" // 提交所有變更
```

> 這些指令是 git 的指令，因為不是主題這邊就不贅述。

```shell
    git remote add origin https://github.com/SimenSimen/example-repo.git // 添加遠端位置
    // 這邊網址要換成你自己的

    git push origin main
```

執行完上述指令，回到 **Github** 網頁，重整之後就可以看到剛剛上傳的內容。

![upload-repo](/images/deploy-to-github-page/upload-repo.png "上傳成功!")

同一頁裡，點擊上方的 `Settings` 選項，點擊 Pages 設定。右邊的`source`選項中，選擇 `Main` (剛剛上傳建立的分支)，點擊儲存。

![add-to-page](/images/deploy-to-github-page/add-to-page.png "加入 Page 設定")

Page 設定就完成了，是不是很簡單呢？設定完分支之後，會看到上方有一列網址，這個網址是 **Github** 幫你生成的網址，可以點擊進入看看部署好的樣子。

![add-to-page2](/images/deploy-to-github-page/add-to-page-2.png "Page 設定完成")

### 網域設定

如果有點擊剛剛 **Github** 產生的網址，我們會發現，整個樣式大走板，圖片看不到，樣子也是最原始的 HTML 。為什麼呢？

這個是因為 **Github** 配給的網址，後面是用路徑區分你的 Github Pages ， 以我的為例：

https://simensimen.github.io/example-repo/ 可以拆成兩個部分

- `https://simensimen.github.io` 我的 Github Pages 基本網址
- `/example-repo/` 這項專案的 Github Pages 位置。

主因是第二個部分，我們在建立 Hugo 靜態資源的時候，如果不特意去設定，預設產生的路徑是沒有第二個部分的：

```html
<!-- 產生出來的路徑 -->
<script src="/js/js-file.js"></script>

<!-- github 檔案實際的位置  -->
<script src="/example-repo/js/js-file.js"></script>
```

解法有兩種：

1. 把 Github Page的第二個部分移除。
2. 可以透過 Hugo 的設定檔 `config.toml` 做設定，加上第二個部分。

因為我們有購買網域，所以可以朝第一個解法的方向去解決，只要把網域導向 Github Pages，那麼從網域進入的用戶來說，就沒有第二個部分了。 **[Page 設定完成]** (上面) 的圖片顯示，Pages設定頁的下方紅色箭頭處有一個 `Custom domain`的設定，透過這個設定可以讓你自訂Github Pages的網域。

#### 加入 Custom domain

我們預先填上剛剛購買的網域，以我的網域舉例填入：`blog.simenstack.tw`，點下 **Save** 儲存。如此一來就完成了。

> 注意：我購買的網域是 *simenstack.tw* ，但我填入的網址 *blog.simenstack.tw*。這是子網域的功能，因為網域只有一個，但又想同時建立其他服務時，可以利用。

#### 設定 Godaddy

回到 Godaday 的網站，點擊右上方鈴鐺右邊的文字，這邊是你的個人資料。點開後可以看到 `我的產品`，點擊進入我的產品頁面。

找到剛剛購買的網址區塊，右上方有三個點，點擊後出現 `管理 DNS` ，點擊進入。


![go-dns](/images/deploy-to-github-page/Dns.png "我的產品 -> 網域 -> 管理DNS")

管理 DNS 葉面讓你可以增加 DNS 紀錄，我們需要在這邊把網址指向我們的 Github Pages。看到下方有個加入的字樣，點下去後選擇想要加入的類型：

類型選擇 `CNAME` ， `host` 填入 **blog** ，指向填入我們的Github Pages基本網址： **simensimen.github.io**，按下儲存。

![create-cname](/images/deploy-to-github-page/create-cname.png "建立 DNS 紀錄")

到這邊就告一個段落啦，接下來就是等待 DNS 生效，我們就可以透過 **blog.simenstack.tw** 瀏覽架設好的部落格了。

#### 網站加入 Https

如果希望有 `Https`，只需要將 `Custom domain` 下方的 `Enforce HTTPS` 打勾即可。

## 完成部署！

只要做完上述的動作，部落格就正式在網路上發布啦，很容易吧。