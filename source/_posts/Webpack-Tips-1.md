---
title: Webpack Tips (1)
author: せいい
top: false
cover: false
toc: true
tags:
  - webpack
categories:
  - Frontend
date: 2021-02-06 22:40:41
summary: webpack系列学习 -- base_demo
---

## 背景
* 当前项目需要storybook显示画面
* 微调配置的时候发现webpack好薄弱啊
* 我是个task驱动型选手

## 学习途径
* 极客时间 视频课程[玩转webpack](https://time.geekbang.org/course/intro/100028901)
* gitchat
* 掘金


## address
* [github](https://github.com/ccloveak/Components_Demo/tree/main/webpack_demo/base_demo)

## メモ
* 自动格式化
* 自动清除dist
    1. 通过插件 clean-webpack-plugin :sparkles:
    2. rm -rf ./dist && webpack
* webpack打包 `yarn run build`
