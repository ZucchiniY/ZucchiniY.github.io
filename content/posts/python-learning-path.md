+++
title = "Python 学习路径"
author = ["Dylan Yang"]
date = 2019-08-07T14:54:00+08:00
categories = ["Python", "生活"]
draft = false
+++

现在 Python 主要在 **前端** 、 **数据分析** 两个方面比较火，相较于其它语言，更灵活，经过一段时间的选择之后，希望可以认真的学习 Python 这门编程语言。


## Python 的级别 {#python-的级别}

对于我们这些程序员来说，总要有一个级别，不然怎么能知道自己在哪个级别呢？


### 一级——了解基本语法 <code>[1/2]</code> {#一级-了解基本语法}

-   [X] 掌握了基本的语法，可以通过 Python 实现常用的需求。不管代码质量怎么样。
-   [ ] [The Python Tutorial 3.7](https://docs.python.org/3.7/tutorial/index.html)


### 二级——熟练使用常用的库 <code>[0/3]</code> {#二级-熟练使用常用的库}

-   [ ] 熟悉常用的 Standard 库的使用。
-   [ ] [The Python Standard Library](https://docs.python.org/3.7/library/index.html)
-   [ ] 熟悉常用的第三方库，要看各自领域中的内容，例如 pandas、flask 等


#### Pythonic 的小技能 <code>[0/8]</code> {#pythonic-的小技能}

-   [ ] 善用内置函数 <code>[0/3]</code>
    -   [ ] enumerate
    -   [ ] reversed
    -   [ ] any all
-   [ ] 小细节 <code>[0/6]</code>
    -   [ ] raise SystemExit
    -   [ ] 文件的 x 模式
    -   [ ] ConfigParser
    -   [ ] defaultdict
    -   [ ] Counter
    -   [ ] nametuple
-   [ ] 使用高级并发工具
-   [ ] 使用装饰器
-   [ ] 使用设计模式
-   [ ] 全局变量
-   [ ] 时间复杂度
-   [ ] 上下文管理器 <code>[0/5]</code>
    -   [ ] 管理锁
    -   [ ] 管理数据库 cursor
    -   [ ] 运算精度
    -   [ ] 同时管理多个资源
    -   [ ] 实现上下文管理协议


### 三级——Pythonic <code>[0/2]</code> {#三级-pythonic}

让编码更优雅，更符合 Python 也就是 Pythonic 而不是用 Python 写 Java 类型的代码，比如 with、for-else、try-else、while-else、yield 等。

另外还需要掌握一些实现原理，了解 Python 在语法层面的一些协方，可以自己实现语法糖。比如（上下文管理器）等。

-   [ ] [[<https://docs.python.org/3.7/reference/index.html>][The Python

Language Reference]]

-   [ ] [Python HOWTOs](https://docs.python.org/3.7/howto/index.html)


### 四级——高级玩法 <code>[0/4]</code> {#四级-高级玩法}

-   [ ] 掌握 Python 的内存机制、GIL限制等
-   [ ] 知道如何改变 Python 的行为
-   [ ] 可以轻松写出高质量的 Python 代码
-   [ ] 能够轻松分辨不同的 Python 代码效率并知道如何优化


### 五级——看透本质 <code>[0/3]</code> {#五级-看透本质}

-   [ ] 阅读 Python 的 C 实现
-   [ ] 掌握 Python 中各种对象的本质，掌握是如何通过 C
-   [ ] 实现对象行为，对于常见的数据结构，掌握其实现细节


## 优雅的 Python {#优雅的-python}

**The Zen of Python**

> Beautiful is better than ugly. <br />
> Explicit is better than implicit. <br />
> Simple is better than complex. <br />
> Complex is better than complicated. <br />
> Flat is better than nested. <br />
> Sparse is better than dense. <br />
> Readability counts. <br />
> Special cases aren't special enough to break the rules. <br />
> Although practicality beats purity. <br />
> Errors should never pass silently. <br />
> Unless explicitly silenced. <br />
> In the face of ambiguity, refuse the temptation to guess. <br />
> There should be one-- and preferably only one --obvious way to do it. <br />
> Although that way may not be obvious at first unless you're Dutch. <br />
> Now is better than never. <br />
> Although never is often better than **right** now. <br />
> If the implementation is hard to explain, it's a bad idea. <br />
> If the implementation is easy to explain, it may be a good idea. <br />
> Namespaces are one honking great idea -- let's do more of those! <br />

<!--quoteend-->

> 优美胜于丑陋 <br />
> 明了胜于晦涩 <br />
> 简洁胜于复杂 <br />
> 复杂胜于凌乱 <br />
> 扁平胜于嵌套 <br />
> 间隔胜于紧凑 <br />
> 可读性很重要 <br />
> 即便假借特例的实用性之名，也不可违背这些规则 <br />
> 不要包容所有错误，除非你确定需要这样做 <br />
> 当存在多种可能，不要尝试去猜测 <br />
> 而是尽量找一种，最好是唯一一种明显的解决方案 <br />
> 虽然这并不容易，因为你不是 Python 之父 <br />
> 做也许好过不做，但不假思索就动手还不如不做 <br />
> 如果你无法向人描述你的方案，那肯定不是一个好方案；反之亦然 <br />
> 命名空间是一种绝妙的理念，我们应当多加利用 <br />


## 路径图 {#路径图}

```python

```

{{< figure src="/images/python-learning-path.png" >}}
