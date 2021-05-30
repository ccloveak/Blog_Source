---
title: Mid-year Summary
author: せいい
top: true
cover: false
toc: true
tags:
  - 工作经验
categories:
  - メモ
  - 生活
date: 2021-05-30 16:03:58
summary: 2021年　中間報告書
---

## 目的

- 对自己这段时间的工作生活做个总结

### 大概目录层次

1. 最近在做什么
2. 这半年做了什么，学到了哪些
3. 下半年预计会做什么，打算加强哪方么样的面的积累
4. 2021 年结束的时候理想的状态

## 今していること

- 用 playwright 为项目搭建 e2e 测试框架 （已完成）

  - 难点是： 在不同的版本依赖中间，找到一个勉强能满足测试需求的平衡（jest, typescript）

- 用 tailwind + antd 搭建适合艺术生展示作品的博客 （进行中）

## この半年間に何をしました

1. 从国际化整理开始，了解项目是怎么实现国际化的
2. x-xsrf 的对应
3. storybook 的编写
4. unit test case 的编写
5. 简单正则的编写
6. react-router 的使用
7. react hooks 的使用
8. 编写自己的 hooks
9. 用 antd protable 展示数据，那段时间疯狂看 antd 的 api 文档，给 antd 提 issue，向 antd 贡献了一个小改善
10. 项目需要动态变色，看了一点 webpack 配置 `config-overrides.js`，简单来说是利用 less 实现动态变色
11. 跟 10 有关的，利用 antd 的 icon 提供的方法，结合 iconfont，找到了一个特别舒爽方法来导入 icon，使用 icon。 `Symbol`。
12. 使用 react-beautiful-dnd 实现了一个嵌套拖拽，不同父级分类的子分类之间可以任意拖拽，父级分类不能拖到子分类
13. 前端渲染树，第一次真的用到递归。foreach 循环，for 循环等等性能上的优劣，以及代码的可读性。提取成 facet 通用组件。
14. 隐约记得调了一部分 storybook 的设定，具体哪部分的忘了。。。
15. 把 e2e 测试导入到项目内部，对比了 playwright，webdriverio，puppeteer,cypress。具体写了 playwright，webdriverio 两套代码。导入项目的过程中还踩了一些坑。
16. 从项目里学到了 eslint prettier 配置，发布了一个脚手架工具 [just-react](https://www.npmjs.com/package/just-react)

## 下半期に何をするか、何を学びたいのか？

- gitlab 工作流 ci/cd 流程
- 编写项目的 e2e test case
- docker
- SEO
- Next.js
- 艺术生向的博客
- aws lambda
- 一门后端框架 django 或者 express
- 一个自动交易机器人
- 网页自动化操作机器人，刷新页面，填写表单，提交表单
- 稍微接触一下前端性能优化

## 2021 年末の理想の姿

- 升值（确定不是错别字） 加薪
- 2021 没有白过
