---
title: "Facebook 留言功能外掛"
date: 2021-12-01T10:51:00+08:00
authors: [Simen]
keywords: "建立留言功能"
---

# 前言

上回已經把部落格架起來了。為了能跟訪客互動，這次我希望能添加留言的功能！所以今天要來研究如何將留言功能加入部落格。

## 外掛選用

Hugo 官網推薦的是 `Disqus` 這個服務。他可以直接和 Facebook、Google 帳戶、Twitter 做連動，非常方便。而 Hugo 看起來也有官方說明，因此就選用 `Disqus`。

## 啟用 Disqus

首先，在安裝之前，我們需要至 Disqus 註冊帳號。選擇下方的選項 "我想在我的網站上安裝 Disqus"。

![create-account-disqus](/images/add-message-plugin/create-account.png "選擇下方的選項")

並且依照要求填完資料。

![create-account-disqus-2](/images/add-message-plugin/create-account-2.png "選擇下方的選項")

> 填完資料後，會要你選擇月費方案，此時先選擇基礎方案即可。