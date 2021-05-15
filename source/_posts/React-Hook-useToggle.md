---
title: React Hook 'useToggle'
author: せいい
top: false
cover: false
toc: true
tags:
  - React
  - Hook
categories:
  - Frontend
date: 2021-05-15 13:07:34
summary: 简单实现开关
---

## 背景

- 需要把一个按钮变成一个开关，点击展开，再点击闭合

## 实现

```typescript
const [expandedState, toggleState] = useToggle(true);

<Button
  onClick={() => {
    toggleState();
    expandedState
      ? () => console.log("执行全部展开的方法");
      : () => console.log("执行全部闭合的方法");
  }}
>
  {expandedState ? (
    <Tooltip title="全部展开">
      <UnFoldSvg className="icon" />
    </Tooltip>
  ) : (
    <Tooltip title="全部闭合">
      <FoldSvg className="icon" />
    </Tooltip>
  )}
</Button>;
```

## 小结

- 不重复造轮子能省下很多不必要的心智开销
- react-use 真的好用
