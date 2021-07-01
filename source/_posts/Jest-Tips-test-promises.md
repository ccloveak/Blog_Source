---
title: Jest Tips 'test promises'
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
date: 2021-07-02 00:55:51
summary: 一次相对顺滑的support经验
---

## 背景
* 发现了同事写的测试有瑕疵，需要他改进测试方法
* 提供追加测试的具体方法

## 具体
* jest test promises [参考](https://jestjs.io/zh-Hans/docs/asynchronous)


```javascript

test('the data is peanut butter', () => {
  return expect(fetchData()).resolves.toBe('peanut butter');
});

test('the fetch fails with an error', () => {
  return expect(fetchData()).rejects.toMatch('error');
});

```

## 小结
* 确实需要从各个纬度保证项目的健壮性
* 看一个同事，先看他代码