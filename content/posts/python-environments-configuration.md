+++
title = "Python 开发环境管理"
author = ["Dylan Yang"]
date = 2019-10-16T19:40:00+08:00
tags = ["virtaulenv"]
categories = ["Python"]
draft = false
+++

目前只对开发环境独立有需求，对不同的 Python 版本没有需要，暂不关心。

虚拟环境主要合适 [virtualenv](https://github.com/pypa/virtualenv) 和
[virtualenvwrapper](https://bitbucket.org/dhellmann/virtualenvwrapper/src/master/)
来管理，在 Windows 系统上，则使用的是
[virtualenvwrapper](https://github.com/davidmarble/virtualenvwrapper-win)
进行管理的。

```shell
# 创建基本环境
mkvirtualenv [env name]
# 删除环境
rmvirtualenv [env name]
# 激活环境
workon [env name]
# 退出环境
deactivate
# 查看所有的环境
workon / lsvirtualenv -b
```

如果是在 Linux 系统下，则需要将 `virtualenvwrapper` 增加到环境变量中，即 `echo "export WORKON_HOME=~/virtualenvs\n source
~/path/to/virtualenvwrapper.sh" >> .zshrc` 或者是其它可以使用的配置文件中。

同样的，在 Windows 环境下，也需要配置，即将 `WORKON_HOME` 配置到环境变量之中

这样就可以在任意的开始开发 Python 程序了。
