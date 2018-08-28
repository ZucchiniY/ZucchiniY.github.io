---
title: "Org mode 下 dot、Python 等无法执行"
date: 2017-07-31T22:10:21+08:00
draft: false
tags: ["Emacs","Org mode"]
categories: ["技术"]
author: "Dylan Yang"
---

# 无法执行的代码

更新之后， *dot* 、 *plantuml* 的代码段在 *Org-mode* 下无法执行，需要引入对应的 *ob-xxx.el* 才能正常执行。

重新编译或者重新下载 *Org* 相关 *package* 即可，也可以使用下面的命令进行更新。

``` lisp
:spacemacs/recompile-elpa
```
<!--more-->