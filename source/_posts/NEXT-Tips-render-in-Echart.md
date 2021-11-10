---
title: NEXT Tips 'render in Echart'
author: せいい
top: false
cover: false
toc: true
tags:
  - Echart
  - Next
categories:
  - Frontend
date: 2021-11-10 23:51:51
summary: 定制echart tooltip小技巧
---

### 背景
* 有个需求需要在 echart的tooltip里进行跳转选项的选择
* 项目框架是 Next

### 问题描述
* 默认的tooltip只能用模版语言写html，虽然导入了tailwind，可以用tailwind画一个ui齐全的样式按钮，但是跳转只能通过a标签跳转，无法走next的link。

### 解决
在tooltip里用 `ReactDOM.render` 渲染一个react节点，这样可以就可以在tooltip里直接写react，可以在里面调用页面上定义的各种方法。


### 伪代码
```typescript
    formatter: function (params: any) {
        setTimeout(() => {
          const root = document.getElementById('toolTip')
          if(root) {
            ReactDOM.render(
             <div>
                // これは　react　code
              </div>,
              root
            )
          }
        }, 0)
        return '<div id="toolTip"></div>'
    }
  },
```
