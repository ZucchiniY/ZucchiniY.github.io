+++
title = "cmder 无法显示中文"
author = ["Dylan Yang"]
date = 2018-08-29T17:04:00+08:00
tags = ["cmder"]
categories = ["笔记"]
draft = false
+++

cmder 默认是不支持中文字符的，可以在 **Setting > Startup > Environment** 下增加一行语言设置：

```shell
set LANG=zh_CN.UTF8
```

然后重启 cmder 即可。
