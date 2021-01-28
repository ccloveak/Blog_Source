---
title: Git Tips 'git bisect'
author: せいい
top: false
cover: false
toc: true
tags:
  - 工作经验
categories:
  - git
date: 2021-01-29 01:10:53
summary: 找问题提交神指令
---

## 背景
* 项目进行到一定程度，突然发现一个错误，而且这个错误还是在之前的某个提交产生的
* 项目leader向我推荐了 "git bisect"指令。。。
* 学名叫 "二分法找bug" -- 沃・孜基・索得

## 主要步骤
1. 找一个肯定没问题的提交 `start`
2. 找一个出问题的提交 `end`
3.
```bash
git bisect start [end] [start]
```
4. 标记正常提交
```bash
git bisect good
```
5. 标记错误提交
```bash
git bisect bad
```
6. 重复 4 5 找到问题提交，预计会出现
```bash
[问题提交] is the first bad commit
```
7. 退出查找
```bash
git bisect reset
```

## 小结
* 你永远不知道会遇到那些神奇的问题
* 不要担心，这些坑前人已经踩过了，而且留下了解决方案
