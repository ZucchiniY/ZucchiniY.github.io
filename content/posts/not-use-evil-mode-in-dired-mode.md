+++
title = "dired 中不使用 Evil"
author = ["Dylan Yang"]
date = 2019-02-25T16:59:00+08:00
tags = ["Evil"]
categories = ["Emacs"]
draft = false
+++

在最近一段时间的使用过程中，发现 Evil 虽然在某些时候要比 Emacs 的操作更方便，但
是在一些 Emacs 的默认使用过程中，还是 Emacs 的更好用，比如说 dired 中。

刚开始希望可以只在 **编辑模式** 中使用 Evil ，比如 org mode 、python mode 这类，但
是在 配置的时候发现，evil hook 并没有启作用。

```emacs-lisp
(use-package evil
  :hook (org-mode . evil-mode))
```

但是这种方案并不能实现在阅读一些相关文档的过程中发现，可以使用另一个方法来修正这
个问题，即在一些特殊的 mode 中关闭 evil 。

```emacs-lisp
(use-package evil
  :config
  (evil-set-initial-state 'dired-mode 'emacs))
```

这样就可以让我们在使用过程中更适合的方式操作了。
