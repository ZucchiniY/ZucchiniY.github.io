---
title: "Emacs 学习之路"
date: 2017-03-20T22:10:21+08:00
draft: false
description: "Emacs 的使用过程，就像是程序员的生涯一样——路漫漫其修远兮，吾将上下而求索。"
tags: ["Emacs","编辑器"]
categories: ["随笔"]
author: "Dylan Yang"
---

# 万物始于 Emacs

最早知道 Emacs 是从编辑器的圣战开始的，即编辑器之神——Vi，和神的编辑器——Emacs。两个编辑器在经历了几十年的战争之后，仍然是编辑世界不可超越的高峰。

但在一开始，我选择的是 Vi，因为在 __*nix__ 中，基本都是有的，在服务器编辑文件——即使是很大的文件，Vi 也可以非常容易的使用，所以在一段时间内，我几乎是跪着使用 Vi 的。

后来随着想用的功能越来越多，而被一些大神安利，我就选择了使用 Emacs 来
记笔记（装逼）。
于是下载了当时正流行的 _Purcell_ 大神的配置，并开始尝试使用，不过没过多少就放弃了。

推荐内容：

- [《一年成为 Emacs 高手（像神一样使用编辑器）》](https://github.com/redguardtoo/mastering-emacs-in-one-year-guide/blob/master/guide-zh.org)
- [Prelude 入门级 Emacs 配置](https://github.com/bbatsov/prelude)
- [Purcell 大神的配置](https://github.com/purcell/emacs.d)

# Emacs 始于 Org

=Emacs= 学习的无疾而终，让我的装逼大计一度沉沦。直到我看到另外两个大神，利用 _Org-mode_ 进行博客写作日程管理，并详细阅读了他们的文章之后，才真正开始了 _Emacs_ 的学习苦旅。

如果说 _Emacs_ 是神的编辑器的话， =Org= 可能是神器之中的神器，随着对 _Org_ 的学习和使用，我从最初的装逼，到后来的逼格提升，都是因为 _Org-mode_ 。

推荐内容：

- [mudan 大神的 Org-mode 入门级手册](https://github.com/mudan/mudan.github.io/blob/master/Emacs/The_Org_Manual/The_Org_Manual.org)
- [mudan 大神的漂亮的文言文排版](https://github.com/mudan/mudan.github.io/blob/master/read/dx.org)
- [Tisoga 大神的 Org + GitHub 的博客教学](http://forrestchang.com/14824097554043.html)

# 终于 Spacemacs 的战争

从最开始的学习，到现在已经习惯于使用 Emacs 的人来说，Emacs 确实是可以提升工具效率的，当然这里要把配置他的时间拿走。
虽然开始使用的原因有所不同，但是大家最后的目标却都是一样的——提高工作（学习）效率。

但是经过了 Emacs 几次配置之后，虽然说不上大神，也就知道了一些 Emacs 的坑是如何解决的。

后来加入了一个 Emacs 的微信群——毫不夸张的说，这是我加入过的群里面质量最高的，学习效果最好的，而且所有的成员都自发的维护群里的闲聊问题，每一次讨论都是提问解决和讨论的过程。

在偶然的一次机会，被安利了一把 Spacemacs，Vi 的操作加上 Emacs 的扩展，不要太吸引人！

推荐关注的大神：

- [Hick](https://github.com/hick) 高质量 _Emacs_ 微信群群主，应该也是发起人，水的人自觉加入闲聊群，是我所有技术相关微信群中质量最高的。
- [子龙山人](https://github.com/zilongshanren) _Spacemacs Rock_ 视频作者，我的配置里抄的最多的就是这位大神的。
- [DarkSun](https://github.com/lujun9972)  黑日大神，大神的文章非常好，多读读，可以找到一些自己需要的配置。
- [tumashu](https://github.com/tumashu) 天然二呆，呆神，之前看到呆神在闲聊群里水，后来又看到呆神在帮忙解决问题，好奇的关注了一下 _GitHub_ ，才发现，竟然这几个好用的 package
  都是呆神写的，而且呆神竟然不是程序员！
  
大神太多了，不一一推荐，如果需要，可以联系 Hick 加一下群，就都有了。

再推荐一下中文的 Emacs 论坛，可以提问，也可以讨论：

- [Emacs China](https://emacs-china.org) 一堆大神在维护的论坛，经常看看，非常好用

# 语乱的 Spacemacs 配置

## 初始

为了更好管理配置，推荐使用 _.spacemacs.d_ 文件夹进行管理配置，而不是使用
_.spacemacs_ 文件。也为了方便后续的扩展。

## 配置说明

目前我的所有配置都放在 _github.com_ 进行托管，目前主要增加了三个配置

[我的 spacemacs 配置:](https://github.com/AboutEmacs/.spacemacs.d)

1. zucchini : 主要用来管理私有配置和全局快捷键
2. zucchini-lisp : 主要用来配置 `/elisp/` 相关内容
3. zucchini-org : 主要用来配置最常使用的 `/org-mode/`

## 可能会遇到的问题

如果是在 Windows 下使用，需要注意几个问题：

  1. 推荐用编译版本，或者用官方网站加部分 _.dll_ 文件来解决
  2. 使用过程中，为了配置的时候好用——更适合 Linux，我是使用在环境变量
    中增加默认的 _HOME_ 的方案，也可以使用其它方法
  3. 直接下载就可以使用，维护的是 _develop_ 分支，后续会慢慢往 _master_
    分支中合并

## 最终选择

在几经周折之后，最后还是选择自己从头开始配置一套 _.emacs.d_ 的内容，但是 _.spacemacs.d_ 的相关内容也没有清楚。
  
  [我的 emacs 原生配置](https://github.com/AboutEmacs/.emacs.d)

# 我的博客地址

如果想看我的博客，可以访问：[我的博客地址](https://zucchiniy.github.io)
