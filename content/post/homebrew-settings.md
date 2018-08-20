---
title: "Homebrew 清华镜像"
date: 2018-08-18T17:04:46+08:00
draft: false
tags: ["Homebrew"]
categories: ["技术"]
author: "Dylan Yang"
---

使用了一段时间的 **Homebrew** 之后，发现网络波动有点大，好多时间都是更新10多分钟，所以就想到了国内镜像问题。

其实无论是什么内容，只要是需要更新的，就有两个优先选择的，一个是清华源，一个是科大源，这两个是最好用的镜像了。

另外一个就是 NPM 的阿里源，这三个源都非常好用。

对于我的使用，主要是两个，一个是 `formula` 索引，另一个是 `bottles`。

`formula` 更新使用

``` shell
cd "$(brew --repo)"
git remote set-url origin https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/brew.git

cd "$(brew --repo)/Library/Taps/homebrew/homebrew-core"
git remote set-url origin https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/homebrew-core.git

brew update
```

<!--more-->

`bottles` 镜像则需要配置到环境变量中，我使用的是 zsh shell 所以配置到 **.zshrc** 文件中

``` shell
echo 'export HOMEBREW_BOTTLE_DOMAIN=https://mirrors.tuna.tsinghua.edu.cn/homebrew-bottles' >> ~/.zshrc
source ~/.zshrc
```

如果你想临时使用的话，则需要在终端中输入 `export HOMEBREW_BOTTLE_DOMAIN=https://mirrors.tuna.tsinghua.edu.cn/homebrew-bottles` ，当然如果你使用的是 bash shell 则可以将其配置到 **.bash_profile** 或者 **.bashrc** 文件中。