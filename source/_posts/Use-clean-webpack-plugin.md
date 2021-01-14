---
title: Use 'clean-webpack-plugin'
author: せいい
top: false
cover: false
toc: true
tags:
  - webpack
categories:
  - Frontend
date: 2021-01-15 01:17:25
summary: 优雅地清理dist
---

## 背景
* 我也不知道为啥会看这个
* 每次构建前需要手动清dist

## 包介绍
* 默认会删除output指定的输出目录

## 使用
```JavaScript
const CleanWebpackPlugin = require('clean-webpack-plugin')

...
...
...
module.exports={
    plugins:[
        new CleanWebpackPlugin()
    ]
}

```
