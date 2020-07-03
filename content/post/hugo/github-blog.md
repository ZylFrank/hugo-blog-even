---
title: "Github Hugo Blog"
date: 2020-07-03T15:42:41+08:00
lastmod: 2020-07-03T15:42:41+08:00
draft: false
keywords: ["Hugo", "even"]
description: "use github deploy hugo blog"
tags: ["Hugo", "Github"]
categories: ["Hugo"]
author: ""

# You can also close(false) or open(true) something for this content.
# P.S. comment can only be closed
comment: false
toc: true
autoCollapseToc: false
postMetaInFooter: false
hiddenFromHomePage: false
# You can also define another contentCopyright. e.g. contentCopyright: "This is another copyright."
contentCopyright: false
reward: false
mathjax: false
mathjaxEnableSingleDollar: false
mathjaxEnableAutoNumber: false

# You unlisted posts you might want not want the header or footer to show
hideHeaderAndFooter: false

# You can enable or disable out-of-date content warning for individual post.
# Comment this out to use the global config.
#enableOutdatedInfoWarning: false

flowchartDiagrams:
  enable: false
  options: ""

sequenceDiagrams: 
  enable: false
  options: ""

---

# Summary

> 使用hugo构建blog，并使用github进行发布。

<!--more-->

## 安装[Hugo](https://gohugo.io/)

### Mac OS

```bash
$ brew install hugo
```

### Window

```bash
$ choco install hugo -confirm
```

### Linux

```bash
$ snap install hugo
```

## 选择[Theme](https://themes.gohugo.io/)

可从该网站选择合适的主题并下载到本地，一般是通过git clone，本文以[`even`](https://github.com/olOwOlo/hugo-theme-even)主题为例构建自己的blog。

通常情况下每个Theme都有一个exampleSite目录为Theme示例，执行一下命令来初始化Blog项目目录

```bash
$ mv hugo-theme-even/exampleSite .
$ mkdir -p exampleSite/themes/even
$ mv hugo-theme-even exampleSite/themes/even.
$ mv exampleSite hugo-blog-even
```

Blog项目目录如下:

```zsh
$ tree -L 3 -I "public"
.
├── config.toml   # 配置文件
├── content   # markdown文件目录
│   ├── about.md
│   └── post
│       ├── default
│       └── hugo
├── resources
│   └── _gen
│       ├── assets
│       └── images
└── themes    # 主题
    └── even
        ├── CHANGELOG.md
        ├── LICENSE.md
        ├── README-zh.md
        ├── README.md
        ├── archetypes
        ├── assets
        ├── i18n
        ├── images
        ├── layouts
        ├── resources
        ├── static
        └── theme.toml
```

也可使用Hugo命令生成站点，然后再引入主题

```bash
$ hugo new site path/to/site
$ cd path/to/site
$ mkdir theme && cd theme
$ git clone git theme
```

## 启动Hugo服务

```bash
$ hugo server
```

服务默认启动在`1313`端口，如果正常访问则表示项目已经搭建好。

## 部署到Github

在Github中创建一个Repository，命名为`<username>.github.io`

修改`config.toml` 文件中的`baseURL` 字段

```bash
baseURL="http://<username>.github.io/"
```

编译Hugo项目

```bash
$ hugo build
```

构建成功后会生成public目录，然后将该目录提交到远端<username>.github.io仓库中

```bash
$ cd public
$ git init
$ git remote add origin you repository url
$ git add .
$ git commit -m "hugo blog"
$ git push -u origin master
```

之后可通过`<username>.github.io` 访问该blog。
