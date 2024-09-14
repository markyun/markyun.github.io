---
title: 玩转Web性能分析, 提升核心体验
date: 2024-09-06 19:56:20
tags: ["Web性能", "性能指标"]
series: ["前端开发"]
category: ["blog","前端"]
featured: true

---

```
  大纲
  ● 背景&目标
    ○ 当我们谈到性能和提高网站“速度”时，具体是指什么呢？
  ● 性能分析 - 理论介绍
    ○ Web Vitals 指标： 是 Google 定义和推广用来衡量和优化网页用户体验的一组标准化性能指标。
    ○ 指标通过三个主要层面：加载性能、交互性、内容加载时视觉稳定性。
  ● 性能分析 - 量化指标（确定好该优化什么）
    ○ 测量现状（客观数据：'CLS' | 'FCP' | 'FID' | 'INP' | 'LCP' | 'TTFB'）
      ■ LCP：Largest Contentful Paint  【最大内容绘制】
      ■ FID： First Input Delay  【首次输入延迟，已废弃】
      ■ INP： Interaction to Next Paint 【交互到下一帧】
      ■ CLS : Cumulative Layout Shift 【累积布局偏移】
      ■ FP：First Paint
      ■ FCP：First Contentful Paint
      ■ TTI ：Time to interactive
      ■ TTFB： Time To First Byte
      ■ ...
    ○ 监控指标（主观体验）
      ■ 这些指标通常需要通过用户反馈、调查或分析来获取。
  ● 性能分析 - 数据评测（监测核心指标，为优化提供数据支撑）
    ○ 工具推荐
      ■ Performance - 面板Chrome  Developers 调试工具
      ■ Lighthouse - Chrome DevTools中集成的开源自动化工具
      ■ web-vitals  npm 库
    ○ 用法示例
      ■ Core Web Vitals 使用示例 （ Web Vitals 的子集 ）
    ○ 优化策略，基于CrUX数据报告，去看对应的文档
      ■ 代码实现层的 JavaScript 渲染层面优化，适合看 Web Vitals ；
      ■ 应用发布层的SSR、SSG、网络、缓存、接口访问优化等，
      ■ 打包构建层的 Code Split & Bundle Analyze 资源加载优化；
  ● 性能优化 - 数据驱动（基于CDP数据分析平台进行提单，长效优化机制）
    ○ 基于针对性的数据dashboard，发现问题。
    ○ 补充：报错监控系统。如 Sentry（是否存在代码错误、业务逻辑、Web安全 等错误）
      ■ Sentry 针对每一种平台都内置了相关的性能数据统计功能。针对前端监控，提供了FCP、LCP、FID、CLS等Web关键数据的统计查看。
      ■ Sentry 也能够每一个页面、每一个Transactions作出性能报告。

```

# 性能分析 - 背景&目标

当我们在谈到网站性能和提高“响应速度”时，具体是**<font>指什么?</font>** 。大家都知道网站性能的重要性。重要归重要，但是如果不好用；具体不好用的原因是啥，是不容易说清的事情。

这是前一段时间在团队分享的如何分享性能问题的文章，博客留档。

**所以，如何衡量和识别\*\***<font>“ 慢 ”</font>\***\*在哪里，是个重要的问题。**


为了解决这个问题，Google 作为浏览器头部厂商，在 2020 年 5 月提出一个的技术概念。


![](https://cdn.nlark.com/yuque/0/2024/png/203859/1725442751522-cf484b4d-b66b-4462-a2f3-d788c6b23332.png)

**<u>Core Web Vitals</u>**

**用来衡量和优化网页体验的，一组标准化性能指标。**


![Google 在 Chromium Blog 中提出的 Web Vitals](https://cdn.nlark.com/yuque/0/2024/png/203859/1725419854759-49750f8c-6ece-4a08-b407-f2595eb123bc.png)

![三个指标 衡量Web可用性](https://cdn.nlark.com/yuque/0/2024/png/203859/1725435072535-5b4fa42d-d0e4-4696-9167-1a368895e52f.png)

![作者也写了这本书](https://cdn.nlark.com/yuque/0/2024/jpeg/203859/1725502344238-c1a0e094-fb5d-4bb1-9bdd-447b7e9959fb.jpeg)

Core Web Vitals 会影响你的应用程序页面的使用体验，以及 Google 上的排名。在这里，我们将深入了解它们是什么，如何衡量它们，以及它们如何影响您的用户体验和搜索排名(Google 会通过真实的用户如何与您的网站互动，并将其报告回其服务器来收集核心 Web Vitals)。

PS: 国内 头部厂商快速跟进了这套标准。

![头部 top3 厂商快速跟进](https://cdn.nlark.com/yuque/0/2024/png/203859/1725419911975-53e02bc6-a693-4cdd-9c1a-1bf42b2f8acc.png)

![](https://cdn.nlark.com/yuque/0/2024/png/203859/1725436376973-073b9212-de52-497c-9829-79198e9501c2.png)

<font style="background-color:rgba(255, 255, 255, 0);">团队负责的产品基于这套标准的一些案例：PTO、eSales </font>

![eSales](https://cdn.nlark.com/yuque/0/2024/png/203859/1725430423808-68530d4c-4cd7-46dc-8449-22507a048372.png)

![PTO](https://cdn.nlark.com/yuque/0/2024/png/203859/1725430510989-926f2718-1436-4cd1-bedf-070d56d2715d.png)

**问题在于：**

_<font style="background-color:rgba(255, 255, 255, 0);">1、基于实验室环境测试，非真实用户体验反馈。</font>_

_<font style="background-color:rgba(255, 255, 255, 0);">2、依赖人工、手动检查问题，并且频率不高。改进前后的对比数据不好直观可视化。</font>_

---

我们做这些，具体要解决什么问题

- 🧑‍💻 开发阶段：Web 前端同学在研发时发现并消灭潜在性能体验问题（实验室环境）
- 🤹 上线之后：Web 应用主动上报的性能数据，通过图表展示健康度，并形成长效优化机制（用户真实环境）

![](https://cdn.nlark.com/yuque/0/2024/png/203859/1725440702530-46b6a7f7-820e-4199-9953-6ead9a0ff03f.png) ![](https://cdn.nlark.com/yuque/0/2024/png/203859/1725441505306-8b67927c-1fed-4e2a-b962-176eb10f0d45.png)

---

## 性能分析 - 量化指标（确定好该优化什么）

Core Web Vitals 通过三个维度：<font>加载性能、交互性、</font>内容加载时的<font>视觉稳定性， </font>通过指标值结合各自权重计算出综合评分。


\*\***指标与用户对网页效果的直观感受相关。\*\*

- 感知加载速度：网页能够以多快的速度加载网页中的所有视觉元素并将其呈现在屏幕上。
- 页面显示速度：网页为了能够快速响应用户互动而加载和执行任何必需的 JavaScript 代码的速度。
- 运行时响应速度：网页加载后，网页对用户互动的响应速度如何。
- 视觉稳定性：网页上的元素是否以用户意想不到的方式偏移，并且可能会干扰用户的互动。
- 流畅性：过渡和动画是否以一致的帧速率渲染，并在一种状态之间流畅地流动。

| **<font> 指标</font>**                    | **Good**    | **<font>Need improvement</font>** | **Poor**   |
| :----------------------------------------------------------------------- | ----------- | -------------------------------------------------------- | ---------- |
| **<font>LCP </font>\*\***最大内容绘制\*\* | **<=2.5s**  | **<font><=4s</font>**             | **>4s**    |
| **<font>INP </font>\*\***交互到下一帧\*\* | **<=200ms** | **<font><=500ms</font>**          | **>500ms** |
| **<font>CLS </font>\*\***累积布局偏移\*\* | **<=0.1**   | **<font><=0.25</font>**           | **>0.25**  |

![示意图](https://cdn.nlark.com/yuque/0/2024/png/203859/1725499630530-b8a2ffce-729d-4cf5-a772-5adad15c25d9.png) ![更好的 CLS 示例](https://cdn.nlark.com/yuque/0/2024/png/203859/1725518184592-a6597059-759a-427a-a7aa-a2057b2ff3ab.png) ![视口大小以及两个渲染帧之间的不稳定元素移动情况，计算偏移值](https://cdn.nlark.com/yuque/0/2024/png/203859/1725499773558-26b461f4-b3ec-4333-8d04-d1aded46e901.png)![Chrome Lighthouse  的权重](https://cdn.nlark.com/yuque/0/2024/png/203859/1725503073462-9482f734-889b-4e4d-9593-16b35b845ebe.png)

主要：

⚡ CLS: Cumulative Layout Shift 【累积布局偏移】

⚡ LCP： Largest Contentful Paint 【最大内容绘制, 最有意义】

⚡ INP： Interaction to Next Paint 【交互到下一帧】

其它：

- _<u>FID</u>_： _<u> First Input Delay 【首次输入延迟，2024 年 3 月已被 INP 替代】</u>_

- FCP： First Contentful Paint 【绘制出首个内容 文本或图片 的时间】

- TTI ： Time to interactive 【页面可稳定交互时间】

- TTFB： Time To First Byte 【加载第一个字节时间】

- FPS： Frame Per Second 【每秒刷新了多少帧】

- TBT： Total Blocking Time <font>【阻塞时间，衡量 FCP 和 TTI 之间的时长；这个数据异常，页面会有卡顿感】</font>

- <font>Speed Index</font>：【从 0 到完全显示出页面的可见填充速度】

* [**<font>首次内容绘制 (FCP)</font>**](https://web.dev/articles/fcp?hl=zh-cn)<font>：衡量从网页开始加载到网页内容的任何部分在屏幕上呈现的时间。</font>_<font>（</font>_[_<font>实验</font>_](https://web.dev/articles/user-centric-performance-metrics?hl=zh-cn#lab)_<font>，</font>_[_<font>字段</font>_](https://web.dev/articles/user-centric-performance-metrics?hl=zh-cn#field)_<font>）</font>_
* [**<font>Largest Contentful Paint (LCP)</font>**](https://web.dev/articles/lcp?hl=zh-cn)<font>：衡量从网页开始加载到屏幕上呈现最大的文本块或图片元素所用的时间。</font>_<font>（</font>_[_<font>实验</font>_](https://web.dev/articles/user-centric-performance-metrics?hl=zh-cn#lab)_<font>，</font>_[_<font>字段</font>_](https://web.dev/articles/user-centric-performance-metrics?hl=zh-cn#field)_<font>）</font>_
* [**<font>Interaction to Next Paint (INP)</font>**](https://web.dev/articles/inp?hl=zh-cn)<font>：衡量与网页进行的每个点按、点击或键盘互动的延迟时间，并根据互动次数选择网页最差（或接近最长的互动延迟时间）作为单个代表性值，以描述网页的整体响应能力。</font>_<font>（</font>_[_<font>实验</font>_](https://web.dev/articles/user-centric-performance-metrics?hl=zh-cn#lab)_<font>，</font>_[_<font>字段</font>_](https://web.dev/articles/user-centric-performance-metrics?hl=zh-cn#field)_<font>）</font>_
* [**<font>总阻塞时间 (TBT)</font>**](https://web.dev/articles/tbt?hl=zh-cn)<font>：衡量 FCP 和 TTI 之间的总时长，在该时间段内，主线程处于阻塞状态的时长足以阻止输入响应。</font>_<font>（</font>_[_<font>实验</font>_](https://web.dev/articles/user-centric-performance-metrics?hl=zh-cn#lab)_<font>）</font>_
* [**<font>Cumulative Layout Shift (CLS)</font>**](https://web.dev/articles/cls?hl=zh-cn)<font>：衡量从网页开始加载到其</font>[<font>生命周期状态</font>](https://developer.chrome.com/blog/page-lifecycle-api?hl=zh-cn)<font>变为隐藏期间发生的所有意外布局偏移的累计得分。</font>_<font>（</font>_[_<font>实验</font>_](https://web.dev/articles/user-centric-performance-metrics?hl=zh-cn#lab)_<font>，</font>_[_<font>字段</font>_](https://web.dev/articles/user-centric-performance-metrics?hl=zh-cn#field)_<font>）</font>_
* [**<font>首字节时间 (TTFB)</font>**](https://web.dev/articles/ttfb?hl=zh-cn)<font>：衡量网络使用资源的第一个字节响应用户请求所需的时间。</font>_<font>（</font>_[_<font>实验</font>_](https://web.dev/articles/user-centric-performance-metrics?hl=zh-cn#lab)_<font>，</font>_[_<font>字段</font>_](https://web.dev/articles/user-centric-performance-metrics?hl=zh-cn#field)_<font>）
  </font>_

这些指标数据怎么来呢？ 并借助工具来可视化它：

![](https://cdn.nlark.com/yuque/0/2024/png/203859/1725438249486-3b0e6a43-4295-4708-82fe-6d13871f0423.png)

具体报告：

PTO 的 CrUX Dashboard 数据 [https://lookerstudio.google.com/u/0/reporting/bbc5698d-57bb-4969-9e07-68810b9fa348/page/WYDQB?params=%7B%22origin%22:%22https:%2F%2Fmy.dito.ph%22%7D](https://lookerstudio.google.com/u/0/reporting/bbc5698d-57bb-4969-9e07-68810b9fa348/page/WYDQB?params=%7B%22origin%22:%22https:%2F%2Fmy.dito.ph%22%7D)

[https://pagespeed.web.dev/analysis/https-my-dito-ph/9xdxjeax7o?hl=zh-cn&form_factor=desktop](https://pagespeed.web.dev/analysis/https-my-dito-ph/9xdxjeax7o?hl=zh-cn&form_factor=desktop)

---

##  性能分析 - 评测工具（监测核心指标并生成报表，为优化提供数据支撑）

- 工具推荐

### 实验室工具：

  - 头铁，什么工具都不用，自己写 Code
  - Performance - Chrome 面板 DevTools 调试工具
  - Lighthouse - Chrome 面板 DevTools 集成的开源自动化工具 \* 它更适合用于开发和持续集成环境，以便在正式版发布前解决性能问题。
  - Web Vitals Chrome 扩展程序（方便）
  - Web-Vitals - Npm 包（JavaScript 库）

### 实地工具：

    - PageSpeed Insights  — 在线测试工具，功能与 Lighthouse 很像。
    - WebPageTest — 在线测试工具，模拟不同地点和设备上的页面加载
    - Chrome CrUX Report  — Chrome 用户体验 报告 （基于 公共数据 给出的体验数据）
    - Google Analytics  (这个要埋点 Google 的代码)

![工具对比，lab 工具多了 TBT 阻塞时间](https://cdn.nlark.com/yuque/0/2024/png/203859/1725436238968-50b7973f-deb7-4bc7-ad2b-ede3334d4f7d.png)

### 用法示例

1、头铁自己写的，方便日常随便跑一下。轻量灵活、秒出结果。
![真自己写？](https://cdn.nlark.com/yuque/0/2024/png/203859/1725438643375-d6ada526-311d-444b-bd72-a656ebd8c5de.png)

![适合开发的时候，想看代码表现](https://cdn.nlark.com/yuque/0/2024/png/203859/1725438722473-da252fde-9653-4e7f-8b6e-1655af103aa0.png)

2、Performance - Chrome 面板 DevTools 调试工具
![](https://cdn.nlark.com/yuque/0/2024/png/203859/1725498753968-7240202e-811f-4645-a1ce-7335720c75cc.png)

3、Lighthouse - Chrome 面板 DevTools 集成的开源自动化工具

PageSpeed Insights 与 Lighthouse 功能基本一致，它提供免费服务，可以分析网页的内容，提出建议，加快网页的速度。它为您提供了关键指标，如第一个内容绘制，总阻塞时间和更多。

  - Lighthouse 因为与浏览器集成，拥有更多堆栈信息，提供针对性建议（如 SEO），更方便定位到代码。（开发用）
  - PageSpeed Insights 结合了实验室和真实用户数据，可以按月提供报告（CrUX），拥有更多对比值。 （都能用）

![](https://cdn.nlark.com/yuque/0/2024/png/203859/1725440521839-ad939f0d-e0e2-4adb-a9da-1ec973e3b438.png)

![](https://cdn.nlark.com/yuque/0/2024/png/203859/1725438249486-3b0e6a43-4295-4708-82fe-6d13871f0423.png?x-oss-process=image%2Fformat%2Cwebp%2Fresize%2Cw_1875%2Climit_0)

4、WebPageTest (简单直观)

![](https://cdn.nlark.com/yuque/0/2024/png/203859/1725441852131-ee53cf89-ab5b-4a51-af76-7341b5058a59.png) ![](https://cdn.nlark.com/yuque/0/2024/png/203859/1725441915942-9ed5915f-7329-4e59-9252-dfc9c837afef.png)

5、Web Vitals 使用示例 （拿到原始数据，方便做数据上报，后续做清洗加工，给业务使用。）

测量 Web Vitals 比你想象的要容易得多 ，这个也是后面，大家需要做的事。
![这个也是后面，大家需要做的](https://cdn.nlark.com/yuque/0/2024/png/203859/1725357326270-70a91818-4640-45de-8444-04cb5f1537bb.png)

![](https://cdn.nlark.com/yuque/0/2024/png/203859/1725440047923-0a89c482-0098-4475-a6d3-4805f39a7618.png)

```json
{
  "name": "LCP",
  "value": 888.,
  "rating": "good",
  "delta": 888.0995,
  "entries": [
    {
      "name": "",
      "entryType": "largest-contentful-paint",
      "startTime": 888.0999999940395,
      "duration": 0,
      "size": 8968,
      "renderTime": 888.0999999940395,
      "loadTime": 0,
      "firstAnimatedFrameTime": 0,
      "id": "",
      "url": ""
    }
  ],
  "id": "v4-1725332024776-5899158889048",
  "navigationType": "reload"
}
```

有开源项目能消费这个数据：

![消费侧](https://cdn.nlark.com/yuque/0/2024/png/203859/1725442037916-2d003036-9811-469c-acb5-f8fc312ebe3b.png)

- 优化策略，基于数据报告点进去看对应的文档即可 (本次带过)
  主要从三个层面： - 代码实现层的 JavaScript <font>渲染性能</font>优化，适合看 Web Vitals ； - 应用发布层的 SSR、SSG、<font>网络、缓存、接口</font>访问优化等， - 打包构建层的 Code Split & Bundle Analyze <font>资源加载类问题</font>优化；

---

## 性能分析 - 数据驱动（基于 CDP 数据报表，长效优化机制）

- 基于针对性的数据 Dashboard，发现问题。

![后续 CDP 添加类似的性能图表](https://cdn.nlark.com/yuque/0/2024/png/203859/1725442116571-081cf798-3b6b-4557-974f-93a909a5fd66.png)
**CDP 应用：**

![CDP的概念](https://cdn.nlark.com/yuque/0/2024/png/203859/1725503327733-748e21ce-36c1-405b-8890-d5be744a2fdf.png)


- 补充：考虑到还有 JavaScript 报错，可以直接搭配专业监控系统；如 Sentry（监控存在代码错误、业务逻辑、Web 安全等）


■ Sentry 针对每一种平台都内置了相关的性能数据统计功能。针对前端监控，提供了 FCP、LCP、FID、CLS 等 Web 关键数据的统计查看。

![总体性能评级](https://cdn.nlark.com/yuque/0/2024/png/203859/1725518024910-9cd5df7b-33d2-416d-b9dc-b765663edb0f.png)

![](https://cdn.nlark.com/yuque/0/2024/png/203859/1725522064730-cf33c8d3-0478-4531-994a-99ca1a46b7be.png)

![](https://cdn.nlark.com/yuque/0/2024/png/203859/1725517693633-37d927b3-b277-43d4-8020-48cf6014ac21.png)

■ Sentry 也能够每一个页面、每一个 Transactions 作出性能报告。

■ React 文档说明：[https://docs.sentry.io/platforms/javascript/guides/react/](https://docs.sentry.io/platforms/javascript/guides/react/)


---

## 其他

一：PTO 不是已经有神策了吗？


神策数据（Sensors Data）作为一个用户行为分析平台，提供了全埋点和点击图等功能，但这些功能主要针对用户行为数据的采集和分析，而不是直接测量上述性能指标。


二：<font>核心网页指标外，还有</font>包括如：移动设备适合性、HTTPS 安全性、插页式广告干扰性 综合网页体验评分。


![](https://cdn.nlark.com/yuque/0/2024/png/203859/1725435521861-fa736184-689b-40ec-a4ef-f57f746d913b.png)


三：W3C 性能工作组在 Navigation Timing API 中定义了一系列页面事件

![从浏览器卸载 旧页面 到 新页面 加载完成的整个过程](https://cdn.nlark.com/yuque/0/2024/png/203859/1725497998399-c76da74a-7f1c-4f76-8f7b-39c5dee92807.png)
<font style="color:rgb(37, 41, 51);">
</font><font style="color:rgb(37, 41, 51);">通过 window.performance.timing 属性获取这些事件的具体时间戳</font>

![通过window.performance.timing属性获取这些事件的具体时间戳](https://cdn.nlark.com/yuque/0/2024/png/203859/1725498035302-bd8bdf8d-f6f2-47cb-9a9e-a8ad3a9aa8c0.png)

- 附配套工具、文档链接
  - https://web.dev/articles/
  - https://developer.chrome.com/docs/lighthouse/
  - [https://web.developers.google.cn/blog/inp-cwv-launch?hl=zh-cn](https://web.developers.google.cn/blog/inp-cwv-launch?hl=zh-cn)
  - [https://developers.google.com/speed?csw=1&hl=zh-cn](https://developers.google.com/speed?csw=1&hl=zh-cn)
  - [<font>https://developer.chrome.com/docs/crux</font>](https://developer.chrome.com/docs/crux?hl=zh-cn)
  - <font>Web 性能会议 </font>[https://perfnow.nl/](https://perfnow.nl/)
  - 一种免费的的 BI 工具，为用户提供了强大的数据分析和可视化功能 [https://lookerstudio.google.com/](https://lookerstudio.google.com/)
  - <font>https://docs.sentry.io/platforms/ </font>
  - <font>优化：</font>[https://blog.bitsrc.io/web-vitals-from-google-to-measure-user-experience-8bf9d33bddbe](https://blog.bitsrc.io/web-vitals-from-google-to-measure-user-experience-8bf9d33bddbe)
  - 如何使用 CrUX BigQuery 数据集 [https://developer.chrome.google.cn/docs/crux/guides/bigquery?hl=zh-cn](https://developer.chrome.google.cn/docs/crux/guides/bigquery?hl=zh-cn)
  - Core Web Vitals 介绍 [https://www.corewebvitals.io/core-web-vitals](https://www.corewebvitals.io/core-web-vitals)
  - Sentry - Web Vitals 指标数据 [https://docs.sentry.io/product/insights/web-vitals/](https://docs.sentry.io/product/insights/web-vitals/)
  - How Core Web Vitals affect SEO [https://vercel.com/blog/how-core-web-vitals-affect-seo-giuMUCEQOZjD5Q1z65gix](https://vercel.com/blog/how-core-web-vitals-affect-seo-giuMUCEQOZjD5Q1z65gix)
