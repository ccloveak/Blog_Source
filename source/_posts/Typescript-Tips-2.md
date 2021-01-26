---
title: Typescript Tips (2)
author: せいい
top: false
cover: false
toc: true
tags:
  - Tpyescript
categories:
  - Frontend
date: 2021-01-26 22:17:55
summary: Tpyescript注释小技巧
---

## 背景（需求）
* 随着业务的复杂，简单命名感觉不够用了
  * 举个简单的例子: 都是table，为什么你可以叫`MemberTable`，我就得叫`***---...table`
* 命名不够用还有个副作用就是接口的名字也更难起了

## 思路
* 虽然我们接口名字一样，但是从不同的文件引入应该不会有问题的吧？？？
* 那就要给接口加注释了。**谁的接口，从哪来，想干嘛**。。。

## 解决
* 接口的注释，类型的注释最好用 ` /**  */ `的形式。
* 效果图
![](ts-tips-2-img.png)

## 小结
* TypeScript真香。
