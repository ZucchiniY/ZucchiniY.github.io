+++
title = "Python无师自通"
author = ["dylanYang"]
date = 2019-02-02T22:44:00+08:00
tags = ["阅读"]
categories = ["Python"]
draft = false
+++

## 作用域 {#作用域}

Python 变量作用域，也会为全局变量和局部作用域，对于全局变量程序可以在任何地方对
全局变量进行写操作，但是在局部作用域中需稍加注意，也就是必须使用 `global` 关键字，
并在其后写上希望修改的变量。

```python
  x = 100
  def f():
    global x
    x += 1
    print(x)

f()
```


## 异常处理 {#异常处理}

Python 中的异常处理是使用的 `try... except` 的方案，在 `try` 从句包含可能会发生
的错误， `except` 从句包含仅在错误发生时执行的代码。如果有多种异常可能出现，则可
以进行多次捕获。

```python
try:
    ...
except (ZeroDivisionError,ValueError):
    ...
```
