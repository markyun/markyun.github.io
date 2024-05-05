---
title: RSS Reader Recommends
date: 2024-04-19 20:00:51
tags: ["前端", "RSS"]
series: ["前端开发"]
category: ["前端"]
featured: true
draft: false
---

In the previous article, I recommended the RSS feeds I have subscribed to, so this time I will supplement with the reader I use to view the content from these information sources.

<!--more-->
PS: I have a weekly front-end technology newsletter called WebCIA Weekly (Web Intelligence Bureau) at https://markyun.github.io/weekly/. From time to time, I share valuable information worth collecting from RSS feeds, including: technical articles, product design, viewpoints, open-source projects, resources and tools, key news, and all things worth paying attention to. This provides insights needed to stay ahead for everyone and also helps me archive information resources. Here, I would like to recommend the tools I use and the sources I subscribe to.


Initially, it was used for weekly technical consulting sharing within the front-end team, but later there were too many restrictions on public sharing on Yuque, so I built my own weekly newsletter website. Therefore, I subscribe to a lot of information sources to recommend as selected content for the newsletter.


# RSS Recommends

RSS 是一种信息订阅服务，把经常浏览的网站聚合在一起，集中查看，不用再逐个打开 B 站、微博、微信、抖音、贴吧等等 APP，直接在 RSS 阅读器里面接收文章、视频、动态…。那么用什么阅读器最方便呢，这里简单说一下我使用心得。


## Feedly (Web)


最开始 我是使用了 Feedly，一款老牌的 RSS 阅读器。它几乎支持所有的 RSS 订阅，而且可以将看到的文章分享到 Pocket 等服务；Feedly 对于国内不能访问的博客，也可以选择 Feedly。使用它配合 Chrome 插件 RSS Subscription Extension，它可以自动识别有 RSS 订阅的网站，体验简直满分。Feedly 的网页和 app 都很好用，但问题还是因为，就是哪个唯一的问题就在国内不能直接访问，而且公司网络禁用 vpn，这点让我放弃了。
https://feedly.com/

## Innoreader (Web)

打开速度较慢，和 Feedly 差不多的功能，功能十分不错，硬说有什么问题的话，UI 风格感觉不太喜欢。
https://www.innoreader.com/

## 原生应用

下面是几个原生 app 推荐

### Reader (推荐)

原生应用、界面简约好看，支持搜索（标题 | 正文）、支持导入配置文件，可以同步 Apple Icloud、支持稍后阅读、导入 GetPocket 等，十分推荐，缺点是 iPhone 端不支持在中国地区使用，可惜。
https://reederapp.com


### NetNewsWire (推荐)

也是原生老牌应用，支持导入配置文件、同步 Apple Icloud。搜索（标题 | 正文）。适用于 Mac、iPhone&iPad。免费开源 非常轻量，Mac 程序包解压后不到 10 MB，而 iOS 应用大小仅 7 MB 左右，设计感稍显一般，而且抓取全文 loading 一会儿，但支持三端同步，在 Mac 上看过的，在 iPhone 端自动也显示已读了，总体满意。
https://netnewswire.com/

### Fluent Reader(推荐)

GitHub 开源、界面简约，搜索（只能搜索标题），支持导入配置文件、支持 Windows、macOS 和 Linux，APP 端也有开源，但不支持导入配置文件（？？），适合在 PC 端观看。
https://github.com/yang991178/fluent-reader


### Readary

原生应用。国产开发，支持 Mac 生态 - 支持导入配置文件、要登录才能用，这点不喜欢。
https://apps.apple.com/us/app/readary/id6449085999?platform=mac




## 自己部署一个 RSS 阅读器（web 版本）

比如：推荐一个极简的 RSS 在线浏览
可以在线部署。但这种模式，更适合看技术文章，因为内容短平快，不需要做一些文章内容的抓取，只需看标题就知道自己想不想看，想看再点进去看原文，对于 code 的显示和点评这方面的交互都更好。
web rss-reader: https://github.com/srcrs/rss-reader



#### 结论：

iOS、iPadOS 和 MacOS 上用 Reeder 或 NetNewsWire 都可以。

Windows 上用 Fluent Reader。


End.