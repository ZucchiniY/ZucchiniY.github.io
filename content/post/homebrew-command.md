---
title: "Homebrew 常用命令"
date: 2018-04-27T22:40:21+08:00
draft: false
tags: ["homebrew"]
categories: ["Mac OS"]
author: "Dylan Yang"
---

# homebrew 安装

使用下面的命令进行安装，但是需要先安装 `curl` :

``` shell
/usr/bin/ruby -e "$(curl -fsSL //
https://raw.githubusercontent.com/Homebrew/install/master/install)"
```


# 常用命令

- 搜索

``` shell
brew search mysql
```

- 查询

``` shell
brew info mysql
```

主要看具体的信息，比如目前的版本，依赖，安装后注意事项等

- 更新

``` shell
brew update
```

这会更新 Homebrew 自己，并且使得接下来的两个操作有意义

- 检查过时

``` shell
brew outdated
```

这回列出所有安装的软件里可以升级的那些

- 升级

``` shell
brew upgrade
```

升级所有可以升级的软件们

- 清理

``` shell
brew cleanup
```

清理不需要的版本极其安装包缓存