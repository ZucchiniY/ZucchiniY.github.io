+++
title = "Emacs 中辅助键设置"
author = ["Dylan Yang"]
date = 2019-07-31T16:50:00+08:00
tags = ["super", "hyper"]
categories = ["Emacs"]
draft = false
+++

使用 Emacs 的人，一般都对 C 和 M 键不陌生，但其实在 Emacs 中，除了常见的 C 和 M 之外，还有 h 和 H 两个辅助键，但是在不同的操作系统中，辅助键的设置是不一样的，但是我们可以通过在 el 文件中设置键位来保证快捷键的一致。

-   windows 系统下

<!--listend-->

```emacs-lisp
(setq w32-pass-lwindow-to-system nil)
(setq w32-lwindow-modifier 'super) ; Left Windows key

(setq w32-pass-rwindow-to-system nil)
(setq w32-rwindow-modifier 'super) ; Right Windows key

(setq w32-pass-apps-to-system nil)
(setq w32-apps-modifier 'hyper) ; Menu/App key
```

-   Mac 系统下

<!--listend-->

```emacs-lisp
(setq mac-command-modifier 'meta) ; make cmd key do Meta
(setq mac-option-modifier 'super) ; make opt key do Super
(setq mac-control-modifier 'control) ; make Control key do Control
(setq ns-function-modifier 'hyper)  ; make Fn key do Hyper
```

这样还有一个问题，在绑定快捷键的时候，super 对应的是 s 前缀，hyper 对应的是 H 的前缀。

```emacs-lisp
(global-set-key (kbd "H-b") 'backward-word) ; 绑定的 Hyper 键
(global-set-key (kbd "s-b") 'backward-word) ; 绑定的 super 键
```
