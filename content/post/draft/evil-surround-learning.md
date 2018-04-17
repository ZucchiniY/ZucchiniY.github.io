---
title: "Surround 笔记"
date: 2018-02-12T22:10:21+08:00
draft: true
tags: ["Vim","Surround"]
categories: ["笔记"]
description: "整理 surround 使用方法。"
author: "Dylan Yang"
---

# surroud 插件

在 vim 的世界中，surround 可以说是被仰望的一个神器，作者是 **Tim Pope** ，在 evil 的世界中，也有一个对应的神器 *evil-surround* 。为了记录这个工具，先从 *surround* 本身说起。

项目的地址如下
- [vim surround](https://github.com/tpope/vim-surround)

| 序号 | 原文本                | 命令    | 新文本                    |
|------|-----------------------|---------|---------------------------|
|    1 | "Hellow world!"       | ds"     | Hellow world!             |
|    2 | [123+456]/2           | cs])    | (123+456)/2               |
|    3 | "Look ma, I'm *HTML!" | cs"<q>  | <q>Look ma, I'm HTML!</q> |
|    4 | if  x > 3 {           | ysW(    | if( x>3 ) {               |
|    5 | my $str = whee!;      | vlllls' | my $str = 'whee!';        |
|    6 | <div>Yo!</div>        | dst     | Yo!                       |
|    7 | <div>Yo!</div>        | cst<p>  | <p>Yo!</p>                |

上面的示例中，添加成对的括号时，如果使用后半括号，是没有空格的，如第 2
个示例，如果使用前半个括号，则是有空格的，如第 4 个示例。另外对于一些
常见的标记，需要记住：

1. t 表示 xml 或者 html 中的 Tag
2. w word
3. W WORD
4. p paragraph

命令表格
- Normal mode
  - ds :: 删除一对配对符号
  - cs :: 替换原来的配对符号
  - ys :: 增加一对配对符号
  - yS :: 增加一对配对符号，并将内容新建一行，并缩进
  - yss :: 为整行增加一对配对符号
  - ySs :: 为整行增加一对配对符号，并新起一行，然后缩进
  - ySS :: 同 ySs

- Visual mode
  - s :: 增加一对匹配符号
  - S :: 增加一对匹配符号，并新起一行，然后缩进

- Insert mode
  - ~<CTRL-s>~ :: 增加一对匹配符号
  - ~<CTRL-s><CTRL-s>~ :: 增加一对匹配符号，并新起一行，然后缩进
  - ~<CTRL-g>s :: 增加一对匹配符号
  - ~<CTRL-G>S :: 增加一对匹配符号，新起一行然后进行缩进

- 修改 =surrounding= 内文本为例：

- ci :: 修改匹配符号内的文本，并进入插入模式
- di :: 剪切匹配符号之间的文本
- yi :: 复制匹配符号之间的文本
- ca :: 同 ~ci~ 但是也修改符号本身
- da :: 同 ~di~ 但是也修改符号本身
- ya :: 同 ~yi~ 但是也修改箱号本身

- b 可以表示小括号，B 表示大括号

* Emacs Evil 模式中的 surround

项目地址 [[https://github.com/emacs-evil/evil-surround][evil surround]]

需要先在 =Emacs= 中增加配置
``` emacs-lisp
  (use-package evil-surround :ensure t :config
      (global-evil-surround-mode 1)
```