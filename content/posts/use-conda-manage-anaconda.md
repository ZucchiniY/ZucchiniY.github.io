+++
title = "使用 conda 管理 Anaconda 环境"
author = ["Dylan Yang"]
date = 2019-07-26T16:18:00+08:00
tags = ["conda"]
categories = ["Python"]
draft = false
+++

## 安装 {#安装}

安装的时候最好选择将 **anaconda** 加入到环境变量中，这样可以直接使用
**conda** 命令来管理包，而不需要增加额外的配置。


## 国内源镜像 {#国内源镜像}

国内使用的话，镜像就还是用 **清华大学开源软件镜像站** ，按步骤安装：

```shell
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main/
conda config --set show_channel_urls yes
```

就可以了，如果是 **conda** 不包含的库的话，还是需要使用 **pip** 命令进行安装的，可以同样配置成清华源

```shell
# 临时使用
pip install -i https://pypi.tuna.tsinghua.edu.cn/simple some-package
# 设为默认值
pip install pip -U
pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple
# 但是这个需要 pip 版本在 10.0.0 以上，如果低的话，可以临时升级
pip install -i https://pypi.tuna.tsinghua.edu.cn/simple pip -U
```


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
