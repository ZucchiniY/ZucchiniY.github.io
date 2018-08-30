---
title: "cmder 无法显示中文"
date: 2018-08-29T23:22:46+08:00
draft: false
tags: ["cmder"]
categories: ["技术"]
author: "Dylan Yang"
---

cmder 默认是不支持中文字符的，可以在 *Setting > Startup > Environment* 下增加一行语言设置：

``` sh
set LANG=zh_CN.UTF8
```

然后重启 cmder 即可。

<!--more-->