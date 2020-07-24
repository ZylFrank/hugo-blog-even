---
title: "Initial React Project"
date: 2020-07-23T16:17:15+08:00
lastmod: 2020-07-23T16:17:15+08:00
draft: false
keywords: []
description: ""
tags: []
categories: []
author: ""

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

# How to create a react project include ant design

<!--more-->

# Summary

> 本文主要记录我使用create-react-app初始化一个使用ant design 前端UI库的项目

## Create Project

[create-react-app Docs](https://create-react-app.dev/)

这里使用create-react-app创建一个项目

```bash
npx create-react-app my-app
cd my-app
npm start
```

## Install ant design

[add antd design to create-react-app project](https://ant.design/docs/react/use-with-create-react-app-cn)

```bash
yarn add antd
npm install antd --save
```

## Customize webpack config

[@craco/craco](https://github.com/gsoft-inc/craco)


这里解释一下为什么要自定webpack配置：
> create-react-app 为了降低开发者的使用难度将webpack配置进行了封装即新创建的项目中webpack配置是不可见的，这样的好处是让开发者无需关系webpack因为facebook已经给你配好了，降低了上手成本。另一方面当你真的有需求需要修改webpack配置时 facebook提供了eject的方式将webpack配置全部编译出来，但这个过程是不可逆的。所以社区出现的react-app-rewired这样的库，让你在不eject的情况下可以自定义webpack配置“使用了 react-app-rewired 之后，等于你得到了项目的配置权，但这表示你的项目将无法得到 CRA 提供的配置“保证”，希望你知道自己要做什么。”

详细配置请见github README

```bash
npm install @craco/craco
yarn add @craco/craco
```

## Integrate ESLint Prettier Stylelint

[Set up create-react-app with: Redux, React Router, Redux Thunk, Prettier, SCSS, Airbnb eslint, Standard stylelint, and CSS modules](https://medium.com/stephenkoo/how-to-set-up-create-react-app-redux-react-router-redux-thunk-prettier-scss-airbnb-eslint-dda0bba5616a)

项目中集成ESLint定制代码规则；使用Prettier格式化代码；使用Stylelint指定样式文件规则

## 配置ESLint

```bash
npm install eslint --save-dev

npx eslint --init

```

1. 使用 `airbnb` 的eslint共享配置

```bash
# 安装 airbnb 需要的相关依赖
npm install eslint eslint-plugin-import eslint-plugin-react eslint-plugin-react-hooks eslint-plugin-jsx-a11y --save-dev

# 安装 airbnb 配置
npm install eslint-config-airbnb --save-dev

# .eslintrc.js
extends: [...others, "airbnb"]
plugin: [...others, "react-hooks"]

# 安装 lint-staged 提供了一组命令行处理eslint
npm install lint-staged --save-dev
```

2. 将eslint命令添加到scripts中

```json
"scripts": {
    "lint:js" : "eslint --cache --ext .js,.jsx,.ts,.tsx --format=pretty ./src"
},
```

## 配置Pritter

1. 安装相关依赖

```bash
npm install prettier eslint-plugin-prettier eslint-config-prettier eslint-formatter-pretty --save-dev

# .eslintrc.js
extends: [...others, "pritter", "pritter/react"]
plugin: [...others, "pritter"]
```

2. 自定义配置 .prettierrc.*

```javascript
module.exports = {
  singleQuote: true,
  trailingComma: 'es5',
  printWidth: 100,
  tabWidth: 2,
};

```

3. 将pritter命令添加到scripts中

```json
"scripts": {
    "prettier": "prettier -c --write \"**/*\"",
    "lint:prettier": "prettier --check \"**/*\" --end-of-line auto",
},
```

## 配置Stylelint

1. 安装相关依赖

```bash
npm install stylelint stylelint-config-prettier stylelint-config-standard stylelint-declaration-block-no-ignored-properties stylelint-prettier --save-dev
```

2. 配置.stylelintrc.*

```javascript
module.exports = {
  extends: [
    'stylelint-config-standard',
    'stylelint-config-prettier',
    'stylelint-prettier/recommended',
  ],
  plugins: ['stylelint-prettier', 'stylelint-declaration-block-no-ignored-properties'],
  rules: {
    'no-descending-specificity': null,
    'function-calc-no-invalid': null,
    'function-url-quotes': 'always',
    'font-family-no-missing-generic-family-keyword': null,
    'plugin/declaration-block-no-ignored-properties': true,
    'unit-no-unknown': [true, { ignoreUnits: ['rpx'] }],
  },
  ignoreFiles: ['**/*.js', '**/*.jsx', '**/*.tsx', '**/*.ts'],
};
```

3. 将stylelint命令添加到scripts中

```json
"scripts": {
    "lint:style": "stylelint --fix \"src/**/*.less\" --syntax less",
}
```
