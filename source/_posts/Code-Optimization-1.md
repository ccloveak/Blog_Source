---
title: Code Optimization (1)
author: せいい
top: true
cover: false
toc: true
tags:
  - ES6
  - 工作经验
categories:
  - Frontend
date: 2021-01-05 23:40:42
summary: 代码优化 -- 命名篇
---

## 背景
* 随着阅历（阅读代码经历）的增加，越来越觉得自己写得代码很垃圾。。。
* 计划对当前项目的代码做小范围的重构优化。

## 理想的命名
1. 有意义的可读的变量名
```javascript
const currentDate = moment().format("YYYY/MM/DD");
const currentPage = pagination['current'];
```
2. 可搜索的变量名（不要为了炫技手动缩短变量名）
```javascript
setTimeout(restart, 86400000);// これはダメ。

//声名为都是大写的常量
const ONE_DAY = 24 * 60 * 60 * 1000;
setTimeout(restart, ONE_DAY);
```
3. 自解释的变量名
```javascript
//可以猜出来contentRange是一串字符串
const [_, pageStart, pageEnd, total] = contentRange.match(
            /(\d+)-(\d+)\/(\d+)/,
        ) as Array<string>;
```

4. 合并功能一致的函数
    * 获取数据的时候可以一次性把数据都给获取了
    * 不要这个地方要"name"了获取个"name"，那个地方要"id"了再获取个"id"

5. 使用默认参数
    * 默认参数比短路逼格更高

6. [CODELF](https://github.com/unbug/codelf)

## 其他
* 随手把注释掉的代码删掉
* 现在用不上的代码以后也用不上
* 现在的代码肯定不能满足以后的需求
* 真的有那么一天需要这段代码了，可以根据文件历史找回代码(git)

## 小结
* 写着写着，忽然发现当前代码可优化的地方不是很多，哈哈哈哈哈
