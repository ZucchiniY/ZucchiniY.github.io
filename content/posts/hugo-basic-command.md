+++
title = "Hugo 常用命令"
author = ["Dylan Yang"]
date = 2018-07-20T11:13:00+08:00
tags = ["hugo"]
categories = ["笔记"]
draft = false
+++

**Hugo是由Go语言实现的静态网站生成器。简单、易用、高效、易扩展、快速部署。**


## 生成站点 {#生成站点}

`hugo new site [path] [flags]`

用来新建一个网站，可以使用一个地址来指定目录生成的位置。


## 新建文章 {#新建文章}

`hugo new [path] [flags]`

用来生成新的文章，基于 ****archetypes/default.md**** 来快速生成。


## 新建主题 {#新建主题}

`hugo new theme [name] [flags]`

创建新的主题，新建的主题是空的，需要加入基础内容才可以使用。


## 本地测试 {#本地测试}

`hugo server [flags]`

用来在本地启动一个Web服务器，常用的命令是 `hugo server` 可以用默认的配置来启动。

如果想指定配置文件，可以使用 `hugo server --config [config]` 文件，如果有一些修改未更新的话，可以在后面加上 `--disableFastRender` 就可以强制生成新的站点了。


## 生成网站 {#生成网站}

`hugo [flags]`

使用的时候，可以像 `hugo server` 一样，指定配置文件，即增加 `--config [config]` 。

现在将生成的过程放到 travis 上去完成，这样可以简化博客过程，只需要专注与写就可以了，具体见 [利用 Travis 自动部署博客](https://zucchiniy.github.io/2018/deploy-blog-by-travis/) 。
