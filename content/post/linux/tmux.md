---
title: "Tmux"
date: 2020-07-16T21:33:32+08:00
lastmod: 2020-07-16T21:33:32+08:00
draft: false
keywords: ["Linux", "Tmux"]
description: "Use Tmux"
tags: ["Tmux"]
categories: ["Linux"]
author: "zhangyunlong"

# You can also close(false) or open(true) something for this content.
# P.S. comment can only be closed
comment: false
toc: true
autoCollapseToc: true
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
# Introduce tmux

<!--more-->

## 安装

### Mac

```bash
brew  install tmux
```

---

## 会话 Session

一个 Tmux 会话中可以包含多个窗口。在会话外创建一个新的会话：

```bash

tmux new -s <session-name>

```

### 会话列表

```bash

tmus ls

```

### 进入会话

```bash

tmus a -t session-name
tmux attach -t session-name

```

### 临时退出但不删除会话

```bash

Ctrl+b d

```

### 在会话内退出并删除session

```bash

Ctrl+b
:kill-session

```

### 在会话外删除指定session

```bash

tmux kill-session -t <name-of-my-session>

```

---

## 窗口 Window

一个 Tmux 会话中可以包含多个窗口。一个窗口中有可以分成多个窗格。


### 新建窗口

```bash

Ctrl+b c

```

### 窗口切换

```bash

Ctrl+b n  # 切换到下一个窗口
Ctrl+b p  # 切换到上一个窗口

```

### 查看当前会话的窗口

```bash

Ctrl+b s
Ctrl+b l

```

### 重命名窗口

```bash

Ctrl+b ,

```

### 在多个窗口里搜索关键字

```bash

Ctrl+b f

```

### 删除窗口

```bash

Ctrl+b &

```

---

## 窗格 Panes

一个tmux窗口可以分割成若干个格窗。并且格窗可以在不同的窗口中移动、合并、拆分。

### 横切 split pane horizontal

```bash

Ctrl+b "

```

### 竖切 split pane vertical

```bash

Ctrl+b %

```

### 上下左右选择pane

```bash

Ctrl+b 方向键上下左右

```

### 调整pane的大小

```bash

Ctrl+b
:resize-pane -U #向上

Ctrl+b
:resize-pane -D #向下

Ctrl+b
:resize-pane -L #向左

Ctrl+b
:resize-pane -R #向右
在上下左右的调整里，最后的参数可以加数字 用以控制移动的大小，例如：

Ctrl+b
:resize-pane -D 5 #向下移动5行
在同一个window里上下左右移动pane

```

### 删除pane

```bash

Ctrl+b x

```
