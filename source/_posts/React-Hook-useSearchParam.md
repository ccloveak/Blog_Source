---
title: React Hook useSearchParam
author: せいい
top: false
cover: false
toc: true
tags:
  - React
  - Hook
categories:
  - Frontend
date: 2021-02-18 22:39:47
summary: useSearchParam使用体验
---

## 背景
* 今天帮同事排查storybook的问题，发现了这个hook

## 优点
* 代码简单，逻辑清晰

## 缺点
* 对storybook不够友好
* 回过头来补充一下，这个缺点可能是我的缺点，需要配置下storybook。。。

## 详细
* 我现在取url上的参数是这么取的
  * 用了 `query-string` ,`react-router-dom` 这两个库

```TypeScript
const parsed = queryString.parse(location.search || '');
const { filter: urlFilterStr } = parsed;
const urlFilters: string = urlFilterStr ? String(urlFilterStr) : '{}';
const formValueObj = JSON.parse(urlFilters);
```
* 同事使用 `useSearchParam`实现就显得比较清爽了

```TypeScript
const filters = useSearchParam('filter');

```

## 大胆猜想
* 感觉底层实现应该很类似，我多加了个初始值 `{}`
* 实际场景里，url中不一定存在 `filter`
* 感觉是`useSearchParam`的返回值有点晚了，storybook都是瞬间渲染的，所以取不到`useSearchParam()`的值

## 小心求证
* [useSearchParam实现](https://github.com/streamich/react-use/blob/master/src/useSearchParam.ts)
* 虽然看不懂他的实现方法，但是盲猜，他是需要经过`window.location`变化后才能取到值，尴尬的是storybook貌似没有模拟`window.location`的变化，可能有但是需要手动添加？！我察觉到这里貌似也有个大坑。

## 小结
* 配置storybook貌似也是个比较艰巨的任务。
* 如果不考虑某些方面的storybook的实现的话，使用`useSearchParam`是一个很不错的选择。
* 其实写完上面这段逻辑是想着自己写个hook优化一下的，奈何时间紧任务重，优先级比较低。
