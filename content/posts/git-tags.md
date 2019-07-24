+++
title = "Git Tags 常用功能"
author = ["Dylan Yang"]
date = 2018-06-04T18:51:00+08:00
tags = ["tags"]
categories = ["Git"]
draft = false
+++

**Git tags 的基础命令的使用。**

-   查看

```shell
git tag
```

-   创建

```shell
git tag tag_name
```

-   推送

```shell
git push origin tag_name
git push --tags # 推送所有 tags
```

-   删除

```shell
# 删除本地
git tag -d tag_name
# 删除远程
git push origin :refs/tags/tag_name
# 需要先删除本地 tag，再删除线上
```

-   拉取

```shell
git fatch origin tag tag_name
```
