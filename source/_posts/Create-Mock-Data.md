---
title: Create Mock Data
author: せいい
top: false
cover: false
toc: true
tags:
  - api
  - storybook
categories:
  - Frontend
date: 2021-01-13 23:59:12
summary: 假数据其乐无穷
---

## 背景

- 之前的开发都是在现成 api 的基础上的（可以通过 api 取数据）
- 现在暂时没有现成的 api，光等后端同学先提供 api 也不现实
- storybook 展示页面也需要假数据

## 解决

- 自己动手，丰衣足食。自己做假数据应该是最优解了。
- 利用 JS 中的 for 循环制作假数据

## 具体步骤

```JavaScript
const members = [];
for (let i = 0; i < 20; i++) {
    members[i] = {
        id: i,
        name: '大郎 吃了 '+ (i + 1).toString()+ ' 颗💊',
        mail: (i < 10 ? 'example' : 'test') + '@example.com',
    };
}
```
