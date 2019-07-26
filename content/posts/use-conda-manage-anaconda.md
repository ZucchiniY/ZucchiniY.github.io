+++
title = "使用 conda 管理 Anaconda 环境"
author = ["Dylan Yang"]
date = 2019-07-26T10:56:00+08:00
tags = ["conda"]
categories = ["Python"]
draft = false
+++

## 安装 {#安装}

安装的时候最好选择将 **anaconda** 加入到环境变量中，这样可以直接使用 **conda** 命令来管理包，而不需要增加额外的配置。

本来在国内，使用清华源比较好，但是因为管理原因，清华源已经不再提供相应的库了，帮将内容移除。


## 包管理 {#包管理}

conda list
: 查看所有的包

conda install package\_name
: 安装包

conda remove package\_name
: 移除包

conda update package\_name
: 升级包

conda search search\_term
: 模糊查询包名

conda update conda
: 更新 **conda** 本身

conda update anaconda
: 更新 **anaconda**

conda update python
: 更新 **Python**
