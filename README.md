<h1 align=center>ASCII-ART Bolg</h1>

<h2 align=center>Web Developer/ Photog/ Work at NanJing</h2>

<h4 align=center>本站内容: 🌈 前端| 📰 文章 | 🌐 多语言 | 🌙 暗色模式 | 📱 移动端适配</h4>

本博客主题来源于 [hugo-ladder](https://github.com/guangzhengli/hugo-ladder-exampleSite) , 中文即阶梯的含义。读书为输入，写作为输出，都是获取知识的阶梯。模板文档中包括了 hugo 所有的安装流程信息，例如如何免费构建独立的博客网站，如何。你可以通过直接访问网站，来获得原生体验。

### 基础使用

    新建博客: hugo new site NewBolgSite

    新建文章: hugo new blog/xxx-文章名.md

    启动博客: hugo server -D


    ---
    title: Git仓库的分支(Branch)规范
    date: 2018-11-27 19:31:30
    tags: ["Git", "代码管理", "规范"]
    series: ["Specification"]
    category: ["Branch"]
    featured: true
    ---

    title 文章题目
    date 发布日期
    tags 标签分类
    series 系列文章，会在下方推荐阅读中推荐同系列文章
    category 分类
    featured 是否在主页面中展示，true or false

## 最小配置

Clone your repository.

Build and run hugo server by `hugo server -D` and open in browser http://localhost:1313/.

```yml
baseURL: 'https://username.github.io' # set https://username.github.io
homepage: 'https://username.github.io' # set https://username.github.io
defaultContentLanguage: 'en' #default language
params:
  brand: HOME # set the brand of your site
  avatarURL: /images/avatar.png # avatar, replace your avatar in the /static/images/
  author: Hugo Ladder # name
  authorDescription: # description
  info:  this is a info # information of your blog site
  favicon: /images/avatar.png # blog site icon，replace your avatar in the /static/images/
  options:
    showDarkMode: true # is show dark mode button
    enableMultiLang: true # is show multi language button
```

Modifying the default configuration. Then push it to your repository.

## Special Thanks

-   Hugo Ladder is inspired by [hugo-paperMod](https://github.com/adityatelange/hugo-PaperMod).
