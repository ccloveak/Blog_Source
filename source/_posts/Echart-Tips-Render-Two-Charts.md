---
title: Echart Tips 'Render Two Charts'
author: せいい
top: false
cover: false
toc: true
tags:
  - Echart
categories:
  - Frontend
date: 2021-11-11 00:10:04
summary: Render two charts with elegant
---

### 背景
* 时间紧，任务重，目前的项目用一个不是很优雅的方式渲染了两张关联性很强的chart
* 我轻微的代码洁癖

### 期待
* 在一张canvas画布里渲染两张图

### 实现逻辑
1. yAxis，xAxis 有一个gridIndex属性
2. grid支持穿对象数组

### 示例代码

* 可以直接在echart的playground查看

```TypeScript
option = {
  legend: {},
  tooltip: {},
  dataset: {
    source: [
      ['product', '2012', '2013', '2014', '2015'],
      ['Matcha Latte', 41.1, 30.4, 65.1, 53.3],
      ['Milk Tea', 86.5, 92.1, 85.7, 83.1],
      ['Cheese Cocoa', 24.1, 67.2, 79.5, 86.4]
    ]
  },
  yAxis: [
    { type: 'category', gridIndex: 0 },
    { type: 'category', gridIndex: 1,axisLabel:{show:false} }
  ],
  xAxis: [{ gridIndex: 0 ,axisLabel:{show:false}}, { gridIndex: 1,axisLabel:{show:false}}],
  grid: [{ left: '150px',right:"35%" },{ left: '65%',right:'0' }],
  series: [
    { type: 'bar', seriesLayoutBy: 'row' },
    { type: 'bar', seriesLayoutBy: 'row' },
    { type: 'bar', seriesLayoutBy: 'row' },
    { type: 'bar', xAxisIndex: 1, yAxisIndex: 1 },
    { type: 'bar', xAxisIndex: 1, yAxisIndex: 1 },
    { type: 'bar', xAxisIndex: 1, yAxisIndex: 1 },
    { type: 'bar', xAxisIndex: 1, yAxisIndex: 1 }
  ]
};

```

### 小记
* 自己定制的乐趣真是其乐无穷。