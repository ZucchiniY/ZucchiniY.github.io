+++
title = "Emacs 功能键配置"
author = ["Dylan Yang"]
date = 2019-02-26T14:10:00+08:00
tags = ["功能键"]
categories = ["Emacs"]
draft = false
+++

Emacs 和 Vim 最大的就是快捷键的体系不同，在 Emacs 中，快捷键要有对应的控制键配合，才能正常使用，比如打开 **Agenda** `C-c a` 一般指的是 `Ctrl + c a` 而在 Emacs 中，使用的控制键主要有以下几种：

```text
s- : supper -
S- : Shift -
M- : Meta - / Alt -
C- : Ctrl -
H- : Hyper -
```

其中 Ctrl、Meta/Alt、Shift这几种快捷键比较常见，但是 supper 这个键就比较少见了，而且在键盘上，一般也看不到，所以我们在配置的时候，需要在配置中声明这几个键被绑定在哪些键上，增加如下的配置：

```emacs-lisp
(setq w32-lwindow-modifier 'supper
      w32-apps-modifier 'hyper)
```

但是如果使用的是 mac 的话又要增加另外的一些配置：

```emacs-lisp
(setq mac-command-modifier 'meta
      mac-option-modifier 'super
      mac-control-modifier 'control
      ns-function-modifier 'hyper)
```

但是这样的情况又有另外一个问题，需要在特定的系统中使用，所以我们要在对应的配置上增加上对系统的判断。这样就可以自由的使用各种快捷键了。
