+++
title = "正确的提交 PR"
author = ["Dylan Yang"]
date = 2017-08-07T11:08:00+08:00
tags = ["PR"]
categories = ["Git"]
draft = false
+++

## 操作流程 {#操作流程}

-   **Fork** 一下原始项目。
-   **clone** 到本地
-   为了追踪原始仓库的更新，需要添加要更新的分支的原始仓库为远程分支

    ```shell
    git remote add upstream <origin>/<xxxx>
    ```

-   创建私有分支 _develop_ ，用来开发项目

    ```shell
    git checkout -b develop
    ```

-   本地 _develop_ 分支提交
-   切换 _master_ 分支，同步原始仓库

    ```shell
    git checkout master
    git pull upstream master
    ```

-   切换本地 _develop_ 分支，合并本地 _master_ 分支并解决冲突
-   提交本地 _develop_ 分支到自己的 _develop_ 分支
-   向原始仓库发起 **Pull Request** 请求
-   等待原作者回复 (接受/拒绝)


## 注意点 {#注意点}

> 在拉取新分支时，最好使用 **rebase** ，需如果使用 **merge** 的话，会增加许多 **commit** 信息，这会降低更新的整洁性。
