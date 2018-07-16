---
title: "JavaScript 中判断是否包含某个字符串"
date: 2018-06-15T15:41:18+08:00
draft: false
tags: ["subString","javaScript"]
categories: ["Web"]
author: "Dylan Yang"
---

# String 对象方法

- `indexOf()`

``` javascript
var str = "123";
console.log(str.indexOf("3") != -1); // true
console.log(str.search("3") != -1); // true
console.log(str.match(reg));// true
```

- `indexOf()` 方法返回指定字符串首次出现的位置，如果未找到，则返回 **-1** 。
- `search()` 方法用来检索字符串中指定的子串，或检索与正则表达式相配置的字符串，如果未找到配置，则返回 **-1** 。
- `match()` 方法可在字符串内检索指定的值，或找到一个或多个正则表达式的匹配。

# RegExp 对象方法

## 创建正则对象

`new RegExp(pattern, attributes);`

- *pattern* 是一个字符串，指定了正则表达式的模式，或者其它正则。
- *attributes* 是一个可选的字符串，包含 **g** 、 **i**、**m**。分别是全局匹配，区分大小写和多行匹配。

正则匹配相关内容见[通配符与正则表达式](https://zucchiniy.github.io/blog/2018/%E9%80%9A%E9%85%8D%E7%AC%A6%E5%92%8C%E6%AD%A3%E5%88%99%E8%A1%A8%E8%BE%BE%E5%BC%8F.html)。

## 使用正则方法查找

- `test()`

``` javascript
var str = "1123";
var reg = RegExp(/3/);
console.log(reg.test(str)); // true
console.log(reg.exec(str)); // null 数组
```

- `test()` 方法用于检索字符串指定的值。返回 **true** 或者 **false** 。

- `exec()` 用于检索字符串中正则匹配，返回一个数组，其中存放匹配的结果，如果未找到，则返回 **null** 。