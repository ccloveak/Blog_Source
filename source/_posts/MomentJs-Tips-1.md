---
title: MomentJs Tips (1)
author: せいい
top: false
cover: false
toc: true
tags:
  - React Plugin
categories:
  - Frontend
date: 2021-02-10 01:08:42
summary: Get time difference.
---

## 問題
* 有需求需要计算时差,并且对结果做一些定制化的美化

## 解決
* momentjs

## code
```Typescript
const currentDate = moment(new Date());
// UTCTime は バックエンドからもらう
const targetDate = moment(UTCTime);
const durationTime = moment.duration(currentDate.diff(targetDate));
const days = duration.asDays();
const months = duration.asMonths();
```

## 参照
* [document](https://momentjs.com/docs/#/durations/)

## 感想
* 中文社区环境确实差，无效信息多得想打人。
