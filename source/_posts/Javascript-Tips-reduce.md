---
title: Javascript Tips 'reduce'
author: せいい
top: false
cover: false
toc: true
tags:
  - ES6
categories:
  - Frontend
date: 2021-07-02 01:13:18
summary: 手动实现reverse()
---

### 背景
* 又一次暴露我是个菜鸡的事实
* 一个小递归

### 需求
```javascript
const arr = [1, 2, [3, [6, 7, 8]], 10, [11, 12]]
const result = [[12, 11], 10, [[8, 7, 6], 3], 2, 1]

```

### 实现
```javascript
function _reverse(array) {
  return Array.isArray(array) ? array.reduce((re, cu)=> [_reverse(cu), ...re], []) : array
}

```
### 小结
javascript 才是最好的语言