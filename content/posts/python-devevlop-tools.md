+++
title = "Python 开发工具"
author = ["Dylan Yang"]
date = 2019-09-27T16:03:00+08:00
tags = ["开发工具"]
categories = ["Python"]
draft = false
+++

经过一段时间的学习和练习，也算对 Python 入了门，现在需要进行项目的开发了，环境配置可以说是开发过程中最重要的一件事，另外一件事就是包管理了，今天在使用的过程中，发现包的升级和管理真的非常麻烦，为了更好的使用这些功能，找到了一个新的工具用来管理 Python 的环境。


## pipx {#pipx}

`pipx` 可以说是解决了一直以来最心烦的一个问题，更新包，可以命题的将所有的包进行更新。而且还支持很多简单实用的功能，可以说是非常良心的一个工具。


## pipenv {#pipenv}

Python 的环境管理主要有几个问题，一个是使用的 Python 的版本，一个是不同环境中的依赖的问题，因为主要是用 Python 3 进行开发，所以可以将版本管理的内容路过了，主要就是开发环境的管理，这里比较好用的工具就是
`virtualenv` 但是这个工具也有一个问题，就是不太简单易读，使用起来比较麻烦，所以在这里有一个补充的工具 `virtualenvwrapper` ，当然如果是在
**Windows** 系统下，使用的则是对应的 `virtualenvwrapper-win` ，两个工具是一样的内容。

后来看到了 `pipenv` 这个工具，工具使用起来非常简单，而且可以按项目启动环境，而且是自动启动的，可以简化了整个工具链的使用，而且并没有区分是哪种类型的内核。


## black isort flake8 {#black-isort-flake8}

对于代码来说，容易阅读的格式，是非常重要的，我们在编写完代码之后，为了有一个统一的风格，使用 `black` 和 `isort` 统一进行代码的格式化操作，而为了使代码符合 **PEP8** 的约定，可以同时使用 `flake8` 进行操作。保证工具之间没有冲突，我们可以增加配置文件中的内容：

```yaml
[isort]
multi_line_output=3
include_trailing_comma=True
force_grid_wrap=0
use_parentheses=line_length=88

[flake8]
ignore = E203，E266，E501，W503
max-line-length = 88
max-complexity = 18
select = B，C，E，F，W，T4
```
