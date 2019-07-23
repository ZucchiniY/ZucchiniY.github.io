+++
title = "Homebrew 入门"
author = ["Dylan Yang"]
date = 2018-04-27T17:19:00+08:00
tags = ["homebrew"]
categories = ["笔记"]
draft = false
+++

## homebrew 安装 {#homebrew-安装}

使用下面的命令进行安装，但是需要先安装 `curl` :

```shell
/usr/bin/ruby -e "$(curl -fsSL //
https://raw.githubusercontent.com/Homebrew/install/master/install)"
```


## 常用命令 {#常用命令}

-   搜索

```shell
brew search mysql
```

-   查询

```shell
brew info mysql
```

主要看具体的信息，比如目前的版本，依赖，安装后注意事项等

-   更新

```shell
brew update
```

这会更新 Homebrew 自己，并且使得接下来的两个操作有意义

-   检查过时

```shell
brew outdated
```

这回列出所有安装的软件里可以升级的那些

-   升级

```shell
brew upgrade
```

升级所有可以升级的软件们

-   清理

```shell
brew cleanup
```

清理不需要的版本极其安装包缓存


## 配置国内镜像 {#配置国内镜像}

使用了一段时间的 **Homebrew** 之后，发现网络波动有点大，好多时间都是更新10多分钟，所以就想到了国内镜像问题。

其实无论是什么内容，只要是需要更新的，就有两个优先选择的，一个是清华源，一个是科大源，这两个是最好用的镜像了。

另外一个就是 NPM 的阿里源，这三个源都非常好用。

对于我的使用，主要是两个，一个是 **formula** 索引，另一个是 **bottles** 。

**formula** 更新使用

```shell
cd "$(brew --repo)"
git remote set-url origin https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/brew.git

cd "$(brew --repo)/Library/Taps/homebrew/homebrew-core"
git remote set-url origin https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/homebrew-core.git

brew update
```

**bottles** 镜像则需要配置到环境变量中，我使用的是 zsh shell 所以配置到 **.zshrc** 文件中

```shell
echo 'export HOMEBREW_BOTTLE_DOMAIN=https://mirrors.tuna.tsinghua.edu.cn/homebrew-bottles' >> ~/.zshrc
source ~/.zshrc
```

如果你想临时使用的话，则需要在终端中输入 `export HOMEBREW_BOTTLE_DOMAIN=https://mirrors.tuna.tsinghua.edu.cn/homebrew-bottles` ，当然如果你使用的是 bash shell 则可以将其配置到 **.bash\_profile** 或者 **.bashrc** 文件中。
