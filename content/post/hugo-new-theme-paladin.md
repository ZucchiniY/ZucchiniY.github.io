---
title: "创建Hugo新主题"
date: 2018-08-22T09:40:38+08:00
draft: true
tags: ["hugo主题"]
categories: ["主题"]
author: "Dylan Yang"
---

# 页面

可以使用 `hugo new theme paladin` 直接创建一个新的主题，然后可以在当前博客中（已经完成了多篇文章，但是还想自己定义一个主题）或者在新主题中增加测试用的项目。

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

### single.html

这个是用来渲染生成的单页文章的，主要是 *content/* 下的内容，可以用来渲染页面的名称、作者、时间和文章的具体内容。

### list.html

这个是用来渲染生成的列表页的，包括文章列表页或者是标签列表和分类列表页。

## partials

这个目录下主要是放需要利用的代码片断，通过 `partial` 方法调用

### header.html

这里主要定义 `<head>` 标签和导航栏 `<nav>` 相关内容。

### footer.html

这里定义了网页脚标位置的相关内容。

# slug 使用

slug 的定义是 title 的一个别称，用来区别文章名称的，如果我们使用的是 title 去链接到某个位置，如果后继我们将文章名称修改了，则这个链接需要同步进行修改，但是如果我们给这篇文章定义一个 `slug` 的话，在调用过程中，使用 slug 去链接文章，则不会出现问题了。

``` yaml
[permalinks]
    post = "/:year/:month/:day/:title/"
```

替换为：

``` yaml
[permalinks]
    post = "/:year/:month/:day/:slug/"
```

但是具体如何使用 slug 去实现链接，还不太会，希望有了解的同学可以邮件给我，邮箱地址: banshiliuli1990@sina.com。