+++
title = "Python 求解质数"
author = ["Dylan Yang"]
date = 2019-04-08T14:39:00+08:00
tags = ["质数求解"]
categories = ["Python"]
draft = false
+++

质数求解是一个非常好的由数据思维转换为计算思维的过程，也是我在初学 C
语言的时候，学的第一个算法，这次在学习 python 的时候，又看到了这个方法，
所以针对原来的谅地，实现了一个 Python 的版本。

```python
import math
def is_prime(n):
    for i in range(2,int(math.sqrt(n)) + 1):
        if n % i == 0:
            return False
    return True
primes = []
for i in range(2,101):
    if is_prime(i) is True:
        primes.append(i)
print(sum(primes))
```
