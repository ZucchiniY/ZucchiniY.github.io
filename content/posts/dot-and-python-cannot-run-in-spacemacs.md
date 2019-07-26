+++
title = "Org mode 中不能执行 dot 、 Python 代码"
author = ["Dylan Yang"]
date = 2017-07-31T11:23:00+08:00
tags = ["recompile"]
categories = ["Emacs"]
draft = false
+++

-   无法执行的代码

更新之后， **dot** 、 **plantuml** 的代码段在 **Org-mode** 下无法执行，需要引入对应的 **ob-xxx.el** 才能正常执行。

重新编译或者重新下载 **Org** 相关 **package** 即可，也可以使用下面的命令进行更新。

```emacs-lisp
:spacemacs/recompile-elpa
```
