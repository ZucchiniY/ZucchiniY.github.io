---
draft: true
---

## hugo blog

``` sh
- content
    - about.md # 关于
    - images/ # 图片
    - posts/ # 文章
        - draft # 草稿
```

## travis 方案

1. 更新 **source** 分支下的文章
2. 上传 [github](https://github.com)
3. 自动生成网站并更新到 **master** 分支

``` yml
sudo: false
os: osx

script:
  - brew install hugo
  - hugo --config jane-config.toml

deploy:
  provider: pages
  skip-cleanup: true
  github_token: $TRAVIS_GITHUB_PAGES
  on:
    branch: source
  local_dir: public  
  repo: ZucchiniY/ZucchiniY.github.io
  target_branch: master
  email: banshiliuli1990@sina.com
  name: ZucchiniY

```
