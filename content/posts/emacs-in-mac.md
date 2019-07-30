+++
title = "Mac 电脑上使用 Emacs"
author = ["Dylan Yang"]
date = 2019-07-29T11:17:00+08:00
tags = ["Mac"]
categories = ["Emacs"]
draft = false
+++

在 Mac 上使用 Emacs 有两个方案，一开始我使用的是
[Emacs For Mac OS X](https://emacsformacosx.com/) , 后来而且更新起来比较麻烦，就改使用
[homebrw-emacsmacport](https://github.com/railwaycat/homebrew-emacsmacport)
，使用下面的命令安装。

```shell
brew tap railwaycat/emacsmacport
brew install emacs-mac
```

但是因为安装之后，需要从 /applications 里找对应的应用，所以需要在安装之后增加一个配置 `ln -s /usr/local/opt/emacs-mac/Emacs.app
/Applications` ，这样之后就可以直接使用了。
