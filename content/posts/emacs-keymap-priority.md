+++
title = "Emacs Keymap 优先级"
author = ["Dylan Yang"]
date = 2019-07-31T17:09:00+08:00
tags = ["keybinds", "priority"]
categories = ["Emacs"]
draft = false
+++

编写 Emacs 的配置文件，无论如何也不能绕开快捷键，对于快捷键一般都是
`define-key` 来实现绑定，但是对于不同的 **keymap** 拥有不同的优先级，了解了这个，就知道了为什么有时候快捷键不启作用了。

key-translation-map
: 最高级，就是把这个键的意义改变了，想使用原来的快捷键，要重新进行绑定

minor-mode-map
: 二级，只在 **minor mode** 激活时启作用，其它时候会被其它的快捷键覆盖掉

local-set-key
: 三级，在 **major mode** 中启作用

global-set-key
: 最弱的级别，但是也是遇简单的方式
