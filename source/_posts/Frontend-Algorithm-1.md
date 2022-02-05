---
title: Frontend Algorithm (1)
author: せいい
top: false
cover: false
toc: true
tags:
  - 代码片段
categories:
  - Algorithm
  - Frontend
date: 2022-02-05 23:07:29
summary: Build a tree from a flat structure.
---

## 背景
* 一个很朴素的需求，前端需要自己生成树结构的数据
* 直观上用递归应该更容易理解
* 不应该在追求性能的路上停下脚步

## 原始数据
```typescript
let array = [
    {id: 1, name: 'A', parentId: 0},
    {id: 2, name: 'B', parentId: 1},
    {id: 3, name: 'C', parentId: 1},
    {id: 4, name: 'D', parentId: 3},
    {id: 5, name: 'E', parentId: 4},
]
```
## 实现
```typescript
const arrayToTree=(items:{id:number,name:string,parentId:number}[])=>{
  let result:any= [];   
  let itemMap = new Map();  // 
  for (const item of items) {
    const id = item.id;
    const parentId = item.parentId;
    if (!itemMap.get(id)) {
      itemMap.set(id,{
        children: [],
      }) 
    }
    itemMap.set(id,{
      ...item,
      children: itemMap.get(id)['children']
    })
    const treeItem =  itemMap.get(id);
    if (parentId === 0) {
      result.push(treeItem);
    } else {
      if (!itemMap.get(parentId)) {
        itemMap.set(parentId,{
          children: [],
        }) 
      }
      itemMap.get(parentId).children.push(treeItem)
    }
  }
  return result;
}
```

## 感受
* 我竟然开始追求起时间复杂度了，不容易啊。

