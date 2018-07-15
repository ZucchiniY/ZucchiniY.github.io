---
title: "Hugo 博客写作与管理"
date: 2018-05-09T22:10:21+08:00
draft: false
tags: ["easy hugo"]
categories: ["Emacs"]
author: "Dylan Yang"
---

# Emacs and Hugo

Hugo 作为一个原生支持 *Org* 的静态站点生成器，是非常好用的，但是和 *Markdown* 比较来看，整体就比较简单了，所以有些时候，可以选择先将 *Org* 转为 *Markdown* 再转成静态站点。

# ox-hugo

但是有些时候，可能直接将 *Org* 导出为 *Html* 然后再对 *Html* 进行渲染，也是一个不错的选择。

方法有很多，但是对于我们来说，**专注写作** 本身才是最重要的，所以我们可以选择使用 [`ox-hugo`](https://ox-hugo.scripter.co/) 来进行转换，这样我们就可以单一的使用 *Emacs* + *Org* 来进行写作，然后再使用工具将文档转换为 *Markdown* ，再进行站点生成。

`ox-hugo` 本身还支持单页博文的生成。即一个 *Org* 文档，利用一个 *heading* 来编写简单的随笔和文章。

![](/images/one-post-per-file.png)

还有一种是单文件配置，如下图：

![](/images/one-post-per-subtree.png)

两种方式都可以方便的生成 *Markdown* 文档，然后渲染成 *html* 。

# Easy Hugo

[`emacs-easy-hugo`](https://github.com/masasam/emacs-easy-hugo) 是一个可以用来进行文章管理的工具，不进行可以新建、生成，还可以发布管理，这都是非常好用的工具。

# Publish

发布的过程一般是这样的：

1. 创建一个新的博文
2. 写博文(@_@)
3. 使用 `ox-hugo` 生成 *Markdown*
4. 使用 `easy-hugo` 预览、管理、调整
5. 发布到远程

# 模板

hugo 文章信息

``` text
#+HUGO_BASE_DIR: ../
#+TITLE: 
#+DATE: `(format-time-string "%Y-%m-%d")`
#+HUGO_AUTO_SET_LASTMOD: t
#+HUGO_TAGS: 
#+HUGO_SECTION: ./
#+HUGO_WEIGHT: auto
#+HUGO_CATEGORIES: 
#+HUGO_DRAFT: false
#+HUGO_MENU: :menu "main" :weight 2001
```