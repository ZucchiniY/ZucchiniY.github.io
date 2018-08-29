---
title: "创建Hugo新主题"
date: 2018-08-22T09:40:38+08:00
draft: false
tags: ["hugo主题"]
categories: ["主题"]
author: "Dylan Yang"
---

# 页面

可以使用 `hugo new theme paladin` 直接创建一个新的主题，然后可以在当前博客中（已经完成了多篇文章，但是还想自己定义一个主题）或者在新主题中增加测试用的项目。

目前所实现的大概样式如下：

![](/images/sn01.png)

![](/images/sn02.png)

<!--more-->

创建之后，在 **themes** 目录下可以看到整个项目结构:

``` yaml
themes/paladin
├── LICENSE
├── archetypes
│   └── default.md
├── layouts
│   ├── 404.html
│   ├── _default
│   │   ├── baseof.html
│   │   ├── list.html
│   │   └── single.html
│   ├── index.html
│   └── partials
│       ├── footer.html
│       └── header.html
├── readme.md
├── static
│   └── css
│       └── stylesheet.css
└── theme.toml

6 directories, 12 files
```

可以看到目录下有一些已经创建好的 *html* 目录，有几个需要编辑的，分别是 **single.html**，**index.html**，**404.html**，**footer.html** 和 **header.html** 这几个文件。

## _default

这里放的，是主要几个网站模板，用来提交一些默认的配置的。

- single.html

这个是用来渲染生成的单页文章的，主要是 *content/* 下的内容，可以用来渲染页面的名称、作者、时间和文章的具体内容。

- list.html

这个是用来渲染生成的列表页的，包括文章列表页或者是标签列表和分类列表页。

## partials

这个目录下主要是放需要利用的代码片断，通过 `partial` 方法调用。

- header.html

这里主要定义 `<head>` 标签和导航栏 `<nav>` 相关内容。

- footer.html

这里定义了网页脚标位置的相关内容。

# 已实现内容

主题参照了[hugo-theme-hiruko](https://github.com/GenkunAbe/hugo-theme-hiruko)的样式，去掉了一些用不到的功能。

主要使用了[bootstrap4](https://getbootstrap.com)，其中的一些内容来源自[阿里巴巴的矢量库](http://www.iconfont.cn)，用起来方便快捷。

# 待实现内容

1. 由于文章过多，目前使用的上一页下一页的样式太过麻烦，所以希望可以实现连续页面的方案。
2. 社交链接想增加到 *about.html* 页面中，准备实现。
3. 增加博客的 *logo* 。