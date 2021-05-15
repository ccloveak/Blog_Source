---
title: Dynamic Theme
author: せいい
top: false
cover: false
toc: true
tags:
  - 工作经验
  - ES6
  - less
  - React
categories:
  - Frontend
date: 2021-05-15 12:04:40
summary: 根据系统主题动态切换site主题
---

## 需求

- 实现 web 端动态切换主题

## 分析

需要实现这个有 2 个步骤

1. 监听 web 端某个属性，什么时候需要切换主题
2. 切换主题的方法

## 实现

1. [prefers-color-scheme](https://developer.mozilla.org/zh-CN/docs/Web/CSS/@media/prefers-color-scheme)

2. window.less.modifyVars

3. 伪代码

```typescript
window
  .matchMedia("(prefers-color-scheme: dark)")
  .addEventListener("change", () =>
    window.less.modifyVars({
      color: color,
    })
  );

window
  .matchMedia("(prefers-color-scheme: dark)")
  .removeEventListener("change", () =>
    window.less.modifyVars({
      color: color,
    })
  );
```

## 实操感受

- 配合 react useEffect 能玩出花
