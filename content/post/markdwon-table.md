---
title: "Markdown 中的表格"
date: 2018-07-12T15:35:21+08:00
draft: false
tags: ["table"]
categories: ["Markdown"]
author: "Dylan Yang"
---

# 默认表格

Markdown 是支持表格的，但是对于表格的支持，只限于简单的表格，复杂的内容并不多。
<!--more-->

``` txt
|目录|内容|
|---|----|
|xxx|xxxx|
|sxe|afda|
```

|目录|内容|
|---|----|
|xxx|xxxx|
|sxe|afda|



# 复杂表格

Markdown 想要支持复杂一些的表格的话，可以支持使用 *JavaScript* 中的 *table* 语法。

- 水平单元格的合并：基于 `colspan` 属性，即使一个单元格占多列的空间
- 纵向单元格的合并：基于 `rowspan` 属性，即使一个单元格占多行的空间

> 居中 `style="text-align:center;"` \\
> 右对齐 `style="text-align:right;"`

## 示例如下

``` javascript
<table>
    <tr>
        <th>目录1</th>
        <th>目录2</th>
        <th>目录3</th>
    </tr>
    <tr>
        <td rowspan="2">内容1</td>
        <td>xxx</td>
        <td>ssss</td>
        <tr>
            <td>sfas</td>
            <td>atadfs</td>
        </tr>
    </tr>
    <tr>
        <td>测试</td>
        <td colspan="2" style="text-align:right;">水平合并</td>
    </tr>
    <tr>
        <td rowspan="2">xxx</td>
        <td>afda</td>
        <td>afadf</td>
        <tr>
            <td colspan="3" style="text-align: center;">afadfa</td>
        </tr>
    </tr>
</table>
```

<table>
    <tr>
        <th>目录1</th>
        <th>目录2</th>
        <th>目录3</th>
    </tr>
    <tr>
        <td rowspan="2">内容1</td>
        <td>xxx</td>
        <td>ssss</td>
        <tr>
            <td>sfas</td>
            <td>atadfs</td>
        </tr>
    </tr>
    <tr>
        <td>测试</td>
        <td colspan="2" style="text-align:right;">水平合并然后右对齐</td>
    </tr>
    <tr>
        <td rowspan="2">xxx</td>
        <td>afda</td>
        <td>afadf</td>
        <tr>
            <td colspan="3" style="text-align: center;">水平合并然后居中</td>
        </tr>
    </tr>
</table>