+++
title = "Python 计算质数提升"
author = ["Dylan Yang"]
date = 2019-04-14T20:28:00+08:00
tags = ["循环语句"]
categories = ["Python"]
draft = false
+++

今天在做 Python 学习的时候，发现自己对于代码的递归和循环的控制，还有实现编程的思考太过简单了，一道简单的编程题，浪费掉了我很多的时间才完成，真的是太不应该了，这倒题是说给定一个数，可以是整数，也可以是浮点数，然后计算这个数之后的5个质数，并输出出来。

现在整理一下思路，求解质数不说了，可以直接使用上次的方案：

```python
def prime(n):
    if n == 1:
        return False
    for i in range(2, int(math.sqrt(n)) + 1):
        if n % i == 0:
            return False
    return True
```

然后就是进入到计算连续的五个数中，首先考虑的是，我需要输出过程中使用五次循环，但是我本身找质数的过程中也应该使用一个计数器循环，所以在最后，应该按下面的方式进行：

```python
start = int(n) + 1
i = 0
while i < 5:
    if prime(start):
        primes.append(str(start))
        i += 1
        start += 1
    else:
        start += 1
print(','.join(primes))
```

所以在最后得到的完整的代码段应该是下面这样的：

```python
import math
def prime(n):
    if n == 1:
        return False
    for i in range(2, int(math.sqrt(n)) + 1):
        if n % i == 0:
            return False
    return True
n = eval(input())
primes = []
start = int(n) + 1
i = 0
while i < 5:
    if prime(start):
        primes.append(str(start))
        i += 1
    start += 1
print(','.join(primes))
```

这次给自己提了个醒，虽然 Python 这门语言特别简单，但是编程这件事儿却手是完全不一样的两个东西。

**希望自己能成为一个高手，而不是一个没用的老手。**

-   changeSet:
    id: 1
    author: your\_name
    changs:
      encoding: utf8
      path: classpath: path/file.sql

\#+END\_SRC
