+++
title = "brew 不常用命令"
author = ["Dylan Yang"]
date = 2019-07-31T16:52:00+08:00
tags = ["homebrew"]
categories = ["笔记"]
draft = false
+++

```shell
brew services list  # 查看使用brew安装的服务列表
brew services run formula|--all  # 启动服务（仅启动不注册）
brew services start formula|--all  # 启动服务，并注册
brew services stop formula|--all   # 停止服务，并取消注册
brew services restart formula|--all  # 重启服务，并注册
brew services cleanup  # 清除已卸载应用的无用的配置
```
