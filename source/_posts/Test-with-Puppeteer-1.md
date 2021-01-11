---
title: Test with Puppeteer (1)
author: せいい
top: false
cover: false
toc: true
tags:
  - Puppeteer
categories:
  - Test
date: 2021-01-11 14:26:16
summary: Puppeteer系列 -- 基本操作
---

## 背景
* 当前项目是使用Jest进行测试的
* 无法对ui组件进行测试
* 无法覆盖到文件的上传下载操作
    * 应该也是我对Jest理解不够造成的

## 基本思路
* 在项目外对项目进行测试
* Node相关的测试方案

## 方案选型
* [Puppeteer](https://zhaoqize.github.io/puppeteer-api-zh_CN/#/)<!-- 多语言之后参考文档链接需要换掉-->

## 基本操作
1. 输入操作&元素点击
    * type
    * click
2. 处理元素
    * $eval
3. 处理多个元素
    * $$()
    * $$eval()
4. 文件上传
    * uploadFile
5. iframe操作
    * page.frames()
6. 拖拽验证码
    * mouse
7. 快捷键操作
    * page.keyborder
8. 浏览器tab页
    * browser.waitForTarget
9. alert窗口
    * dialog

## 参考
* [bilibili](https://space.bilibili.com/306107070/channel/detail?cid=79090)
    * 万能的b站 给我力量

## 小结
* 虽然拿Puppeteer用来做测试，不过貌似改改可以变身爬虫。
* 柳暗花明又一村，可以把 Puppeteer整合到Jest中。[Jest](https://jestjs.io/docs/en/puppeteer)
