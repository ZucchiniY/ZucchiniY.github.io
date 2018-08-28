---
title: "XPath 使用笔记"
date: 2016-01-06T22:10:21+08:00
draft: false
tags: ["Selenium"]
categories: ["技术"]
author: "Dylan Yang"
---

# xpath 语法
XPath 是 XML 的查询语言，和 SQL 的角色很类似。以下面 XML 为例，介绍 XPath 的语法
<!--more-->

``` html
<?xml version="1.0" encoding="ISO-8859-1"?>
<catalog>

   <cd country="USA">
      <title>Empire Burlesque</title>
      <artist>Bob Dylan</artist>
      <price>10.90</price>
   </cd>

   <cd country="UK">
     <title>Hide your heart</title>
     <artist>Bonnie Tyler</artist>
     <price>9.90</price>
   </cd>

   <cd country="USA">
     <title>Greatest Hits</title>
     <artist>Dolly Parton</artist>
     <price>9.90</price>
   </cd></catalog>

</catalog>
```

## 定位节点

XML 是树状结构，类似档案系统内数据夹的结构，XPath 也类似档案系统的路径命名方式。不过 XPath 是一种模式(Pattern)，可以选出 XML 档案中，路径符合某个模式的所有节点出来。例如要选 catalog 底下的 cd 中所有 price 元素可以用:

``` html
/catalog/cd/price
```

如果 XPath 的开头是一个斜线（/）代表这是绝对路径。如果开头是两个斜线（//）表示文件中所有符合模式的元素都会被选出来，即使是处于树中不同的层级也会被选出来。以下的语法会选出文件中所有叫做 cd 的元素（在树中的任何层级都会被选出来）：

``` html
//cd
```

## 选择未知的元素

使用星号（Wildcards,*）可以选择未知的元素。下面这个语法会选出/catalog/cd 的所有子元素：

``` html
/catalog/cd/*
```

以下的语法会选出所有 catalog 的子元素中，包含有 price 作为子元素的元素。

``` html
/catalog/*/price
```

以下的语法会选出有两层父节点，叫做 price 的所有元素。

``` html
/*/*/price
```

以下的语法会选择出文件中的所有元素。

``` html
//*
```

要注意的是，想要存取不分层级的元素，XPath 语法必须以两个斜线开头(//)，想要存取未知元素才用星号(*)，星号只能代表未知名称的元素，不能代表未知层级的元素。

## 选择分支

使用中括号可以选择分支。以下的语法从 catalog 的子元素中取出第一个叫做 cd 的元素。XPath 的定义中没有第 0 元素这种东西。

``` html
/catalog/cd[1]
```

以下语法选择 catalog 中的最后一个 cd 元素：（XPathj 并没有定义 first() 这种函式喔，用上例的 [ 1 ] 就可以取出第一个元素。

``` html
/catalog/cd[last()]
```

以下语法选出含有 price 子元素的所有/catalog/cd 元素。

``` html
/catalog/cd[price]
```

以下语法选出 price 元素的值等于 10.90 的所有/catalog/cd 元素

``` html
/catalog/cd[price=10.90]
```

以下语法选出 price 元素的值等于 10.90 的所有/catalog/cd 元素 的 price 元素

``` html
/catalog/cd[price=10.90]/price
```

## 选择一个以上的路径

使用 Or 操作数(|)就可以选择一个以上的路径。例如：

``` html
/catalog/cd/title | catalog/cd/artist
```

选择所有 title 以及 artist 元素

``` html
//title | //artist
```

选择所有 title 以及 artist 以及 price 元素

``` html
//title | //artist | //price
```

## 选择属性

在 XPath 中，除了选择元素以外，也可以选择属性。属性都是以@开头。例如选择文件中所有叫做 country 的属性。

``` html
//@country
```

选择所有含有 country 这个属性的 cd 元素：

``` html
//cd[@country]
```

以下语法选择出含有属性的所有 cd 元素

``` html
//cd[@*]
```

以下语法选择出 country 属性值为 UK 的 cd 元

``` html
//cd[@country='UK']
```

选择多个属性

``` html
//cd[@country='UK'][@name='hyddd']
```