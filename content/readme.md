---
draft: true
---

# 博客备份文档

## 博客优先更新这个，然后再发布

### hugo blog

``` sh
- content
    - about.md # 关于
    - images/ # 图片
    - post/ # 文章
        - draft # 草稿
```

## travis 方案 (待实现)

1. 更新 context 内容
2. 将 `*.md` 内容复制到 hugo-blog/content/post 下
3. 在 hugo-blog 下执行 `hugo` 命令
4. 将 hugo-blog/public 下的内容发布到 zucchiniy.github.io 的 master 分支