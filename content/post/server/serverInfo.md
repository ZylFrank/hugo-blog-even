---
title: "Server Info"
date: 2020-07-16T21:10:11+08:00
lastmod: 2020-07-16T21:10:11+08:00
draft: false
keywords: ["Server"]
description: "Record Server Info"
tags: ["Server"]
categories: ["Server"]
author: "zhangyunlong"

# You can also close(false) or open(true) something for this content.
# P.S. comment can only be closed
comment: false
toc: true
autoCollapseToc: true
postMetaInFooter: false
hiddenFromHomePage: true
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

# 记录一些服务器信息

<!--more-->

## 内网服务器连接网络

```bash

ssh -R 4000:192.168.100.2:8888 viathink@172.16.40.116

export http_proxy=http://localhost:4000
export https_proxy=http://localhost:4000

git config --global http.proxy http://localhost:4000

```

## AMGT服务器登录

```bash

ssh -p 2201 ubuntu@amgt-ts.plantdna.site
ssh -p 2201 ubuntu@49.233.41.94

```

## 青云服务器

### 部署的系统有

- [CloudLims:仪器管理系统](http://maizedna.cn:8085)
  - [接口文档](http://maizedna.cn:9091/apidocs/index.html)

- [Login: 安全登录系统](http://maizedna.cn:8084)
- [考勤登记系统](http://maizedna.cn:8082)
- [TSTP:定点测序分析平台](http://maizedna.cn:8083)

```bash

ssh viathink@maizedna.cn

```

## Nginx配置服务器

```bash

ssh -p 2201 viathink@192.168.17.157

```

## SWMS外网访问服务器

```bash

ssh viathink@192.168.17.229

```

## SWMS内网访问服务器

```bash

ssh viathink@172.16.42.111

```