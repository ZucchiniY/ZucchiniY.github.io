+++
title = "ox-hugo 配置"
author = ["Dylan Yang"]
date = 2019-02-26T16:08:00+08:00
tags = ["Emacs", "hugo"]
categories = ["笔记"]
draft = false
+++

在工作中， **Org-Mode** 本身要比 **Markdown** 有用的多，而且使用过程也会比
**Markdown** 好用，但是说实话，程序员多多少少都要会 **Markdown** 的语法。

**Markdown** 我更希望只用在写 Readme 文档之中，其它的如果可以的话，最好都可以用
**Org-Mode** 替代。

最早的时候，我是使用 **Org-Mode** 默认的导出 **Html** 的方法写博客，然后部署到
**GitHub** 上的，但是随着许多静态博客生成器的出现，可以让我们更多的专注于写文章本
身而减少对工具的依赖，后面也尝试过 **Hexo** 这个工具，非常好用，但是在了解了
**Hugo** 这个工具之后，我就选择了 **Hugo** 就是因为它支持 **Org-Mode** 直接生成博客，
但是在使用中发现，对 **Org-Mode** 的支持非常低，而且和 **Markdown** 这种形式沅法比，
后来在一些文章中读到了关于 **ox-hugo** 的介绍，决定使用 **ox-hugo** 来将文章从
_.org_ 格式转换成 _.md_ 格式。

下面是需要在 Org 文件顶端增加的配置：

```org
#+HUGO_BASE_DIR: ~/workspace/org/blog/path
#+SEQ_TODO: TODO DRAFT DONE
#+PROPERTY: header-args :eval no
```

其中 `#+HUGO_BASE_DIR:` 是用来设置导出的位置的，默认会增加
`content/postt/` 路径，所以只需要配置到对应的博客的根目录即可。

在导出的时候，如果是 TODO 则认为没有写完，不进行导出，如果是 DONE 则导
出，DRAFT 则是草稿。

对于相关的配置可以阅读 **ox-hugo** 本身的介绍文档
[https://ox-hugo.scripter.co/](https://ox-hugo.scripter.co/) 。当然也可以通过这篇文章了解如何进行配置。

配置如下：

```emacs-lisp
(with-eval-after-load 'org-capture
  (defun org-hugo-new-subtree-post-capture-template ()
    "Return `org-capture' template string for new Hugo post."
    (let* ((date (format-time-string (org-time-stamp-format :long :inactive) (org-current-time)))
           (title (read-from-minibuffer "Post Title: "))
           (file-name (read-from-minibuffer "File Name: "))
           (fname (org-hugo-slug file-name)))
      (mapconcat #'identity
                 `(
                   ,(concat "* TODO " title)
                   ":PROPERTIES:"
                   ,(concat ":EXPORT_FILE_NAME: " fname)
                   ,(concat ":EXPORT_DATE: " date)
                   ":END:"
                   "%?\n")
                 "\n")))

  (add-to-list 'org-capture-templates
               '("h"
                 "Hugo post"
                 entry
                 (file+olp "~/workspace/org/blog/hugo-posts.org" "Blog Ideas")
                 (function org-hugo-new-subtree-post-capture-template))))
```

通过上面这个，就可以生成对应的 capture templates 了，而且在执行
`org-export-dispatch` 时就可以看到 hugo 导出配置了。
