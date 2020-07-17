---
title: "Docker"
date: 2020-07-13T15:15:13+08:00
lastmod: 2020-07-13T15:15:13+08:00
draft: false
keywords: ["Docker"]
description: ""
tags: ["Docker"]
categories: ["Docker"]
author: "zhangyunlong"

# You can also close(false) or open(true) something for this content.
# P.S. comment can only be closed
comment: true
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

> Docker系统部署。

<!--more-->

## ubuntu安装Docker

> sudo snap install docker

使用docker命令如果出现如下错误：

```bash
Got permission denied while trying to connect to the Docker daemon socket at unix:///var/run/docker.sock: Get http://%2Fvar%2Frun%2Fdocker.sock/v1.40/containers/json: dial unix /var/run/docker.sock: connect: permission denied
```

解决方案：

```bash
sudo groupadd docker #添加docker用户组
sudo gpasswd -a $USER docker #将当前用户添加至docker用户组
newgrp docker #更新docker用户组
```

## 安装docker-compose

[docker-compose install](https://docs.docker.com/compose/install/)

```bash
sudo apt install curl

sudo curl -L "https://github.com/docker/compose/releases/download/1.26.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose

sudo chmod +x /usr/local/bin/docker-compose

sudo ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose

```

## 宿主机与容器间的文件交换

```bash
docker cp CONTAINER:/PATH OUT_PATH
```

## 镜像的导入导出

```bash
docker save -o image.tar image:version
docker load --input image.tar
```

## 使用镜像内部命令

```bash
docker run --rm  -v `pwd`:/mnt/app -w /mnt/app node:8.16.1 npm run build
```
