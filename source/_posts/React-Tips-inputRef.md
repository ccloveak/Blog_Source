---
title: React Tips 'inputRef'
author: せいい
top: false
cover: false
toc: true
tags:
  - 工作经验
  - React
categories:
  - Frontend
date: 2021-07-02 00:47:11
summary: 通过ref精准控制输入框
---

## 背景
* 从 2周一次的 lightning talk学到的小技巧
* 通过ref定位到光标所在位置

## 代码

```typescript
const inputRef = React.useRef<any>(null);

const position = inputRef.current.resizableTextArea.textArea.selectionStart;

```

## 小结
小黄姐牛逼到爆炸了