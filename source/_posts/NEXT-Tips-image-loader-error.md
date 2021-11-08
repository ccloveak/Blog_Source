---
title: NEXT Tips 'image loader error'
author: せいい
top: false
cover: false
toc: true
tags:
  - NEXT
  - React
categories:
  - Frontend
date: 2021-11-09 01:27:51
summary: 解决image loader报错
---

## 背景
* 新的项目使用next开发，从头搭了一套next+ant design+tailwind开发框架，预感到会遇到奇奇怪怪的问题

## 问题
* 在构建过程中出错(开发环境没有问题)

```bash

Error: Image Optimization using Next.js\' default loader is not compatible with next export.
Possible solutions:

```


## 解决
```javascript
// next.config.js
// 添加下面代码
images: {
    loader: "imgix",
    path: "https://noop/",
},

```


## 相关链接
* [github issue](https://github.com/vercel/next.js/issues/21079)