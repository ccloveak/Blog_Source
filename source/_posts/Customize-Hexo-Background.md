---
title: Customize Hexo Background
author: せいい
top: false
cover: false
toc: true
tags:
  - Hexo
categories:
  - Frontend
date: 2021-01-17 11:57:35
summary: 定制喜欢的Hexo背景
---

## 背景
* 怎么说也是做前端的，这么丑的界面有点受不了了
* 放松一下，对blog进行美化

## 踩坑步骤
* 关闭图片
* 关闭动态背景
* 安装 [canvas-nest](https://github.com/ccloveak/canvas-nest.js/blob/master/README-zh.md)
* 拷贝 `node_modules/canvas-nest.js/dist/canvas-nest.js`
* 然后发现貌似主题内置了 canvas-nest。。。hhhhh尴尬了
* 在主题设置里调一下canvas-nest的配置
* 具体操作细节在这次的commit里
