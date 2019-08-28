+++
title = "Emacs 快捷键配置方案"
author = ["Dylan Yang"]
date = 2018-05-05T11:04:00+08:00
tags = ["keybinds"]
categories = ["Emacs"]
draft = false
+++

**Emacs 的快捷键和 Vim 的快捷键是编辑器中的两坐高山，其中 Emacs 的快捷键主要有四类。**


## 四大类型 {#四大类型}

-   全局快捷键

<!--listend-->

```emacs-lisp
(global-set-key (kdb "a") 'command)
```

-   全局映射键

<!--listend-->

```emacs-lisp
(define-key key-translation-map (kbd "a") (kdb "b"))
```

-   Major-mode 局部快捷键

<!--listend-->

```emacs-lisp
(local-set-key (kdb "a") 'command)
```

-   Minor-mode 局部快捷键

<!--listend-->

```emacs-lisp
(define-key your-minor-mode-map (kbd "a") 'command)
```


## 删除、禁用快捷键 {#删除-禁用快捷键}

```emacs-lisp
(global/local-unset-key (kbd "a"))
(global/local-set-key (kbd "a") 'ignore/nil)
```


## 键冲突与解决 {#键冲突与解决}

最方便的解决方案是找一个空置的 **prefix** 键，先映射到这个键上，再全局或者局部设置它。


### 先映射到悬空键上 {#先映射到悬空键上}

```emacs-lisp
(define-key key-translation-map (kbd "a") (kbd "M-g A"))
```


### 全局或者局部设置 {#全局或者局部设置}

```emacs-lisp
(global/local-set-key (kbd "M-g A") 'command)
```


## 快捷键优先级 {#快捷键优先级}

**key-translation-map > minor-mode-map > local-set-key > global-set-key**


### 设置局域快捷键 {#设置局域快捷键}

```emacs-lisp
(defun f-python-mode ()
  (local-set-key (kbd "C-x C-e")'f-python-shell-send-line)
  (local-set-key (kbd "M-g C-y") 'f-python-shell-send-line))
(add-hook 'python-mode-hook 'f-python-mode)
```

**注意** 当键进行重新绑定后，还应该将之前的功能重新绑定到另一个键上。


## Minor Mode Map {#minor-mode-map}

```emacs-lisp
(define-minor-mode visual-mode
  :init-value nil
  :global t
  :keymap (make-sparse-keymap)
  (if (not visual-mode) (setq cursor-type 'bar)
    (setq cursor-type 'box)))
(define-key visual-mode-map (kbd "h") 'mark-paragraph)
```

定义之后，可以利用 `define-key` 来设置当前快捷键。然后在需要启用 **Visual mode** 的时候可以启用这个 **minor mode** 的相关快捷键。
