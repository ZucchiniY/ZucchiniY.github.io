---
title: "Ajax 关闭异步请求"
date: 2018-06-20T17:04:12+08:00
draft: false
tags: ["ajax 同步请求"]
categories: ["Web"]
author: "Dylan Yang"
---

在代码中，因为进行了后台的取值操作，导致有些内容还未加载就执行到了新的地方，所以想着 ajax 的异步关闭来解决。

<!--more-->

`async` 设置为 **false** 的时候，变成同步操作，默认(**true**)为异步操作。

``` js
$.ajax({
    cache: false,
    async: false,   // 太关键了，学习了，同步和异步的参数
});
alert("2");
```