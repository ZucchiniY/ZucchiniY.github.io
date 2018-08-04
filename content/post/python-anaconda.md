---
title: "使用conda管理anaconda环境"
date: 2018-08-04T23:17:35+08:00
draft: false
tags: ["anaconda"]
categories: ["技术"]
author: "Dylan Yang"
---

# 安装

安装的时候最好选择将 **anaconda** 加入到环境变量中，这样可以直接使用 `conda` 命令来管理包，而不需要增加额外的配置。

# 设置国内镜像

**无论做什么，先设置国内镜像都是最重要的事情。**

这里推荐用[清华的源](https://mirrors.tuna.tsinghua.edu.cn/help/anaconda/)的配置。

在命令行中按清华源的配置进行设置：

``` shell
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main/
conda config --set show_channel_urls yes
```

然后可以进行包的更新：

`conda upgrade --all`

之后就可以使用 `conda` 进行包管理了。

# 包管理

- `conda list` 查看所有的包 
- `conda install package_name` 安装包
- `conda remove package_name` 移除包
- `conda update package_name` 升级包
- `conda search search_term` 模糊查询包名
- `conda update conda` 更新 `conda` 本身
- `conda update anaconda` 更新 **anaconda**
- `conda update python` 更新 **Python**