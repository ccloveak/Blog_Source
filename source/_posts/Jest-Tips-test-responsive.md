---
title: Jest Tips 'test responsive'
author: せいい
top: false
cover: false
toc: true
tags:
  - Jest
  - 工作经验
categories:
  - Frontend
  - Test
date: 2021-06-20 12:48:24
summary: 一次非常顺滑的support经历
---

## 背景
* 发现了同事写页面时候的一个小bug，需要他追加测试
* 在同事演示手机版时发现了另一个小bug，需要他再次追加测试
* 提供追加测试的具体方法


## 具体
* jest test responsive [参考](https://medium.com/@akilanoop/make-the-best-out-of-unit-testing-with-jest-and-react-testing-library-99f361c2ce0f)
  
* 错误对应 [参考](https://stackoverflow.com/questions/46221210/jest-enzyme-how-to-test-at-different-viewports/59307258#59307258)

```javascript
  Object.defineProperty(window, 'innerWidth', 
          {
            writable: true, 
            configurable: true, 
            value: 375
          }
  )
```

## 小结
* 手把手保姆级贴身服务
* 操作工具人完成对项目品质的保障，我飘了，我飘了。