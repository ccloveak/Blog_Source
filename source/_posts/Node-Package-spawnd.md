---
title: Node Package 'spawnd'
author: せいい
top: false
cover: false
toc: true
tags:
  - node
  - playwright
categories:
  - Backend
  - E2E
date: 2021-06-20 12:13:54
summary: playwright中的进程管理
---

## 背景
* 一个很朴素的e2e需求：启动服务器，进行e2e测试，关闭服务器
* 尝试过很多方法，还是从playwright的[官方配置](https://github.com/playwright-community/jest-playwright#start-a-server)中找到了灵感 

## 具体
1. playwright是通过spawnd来做服务器相关的进程管理的
2. Spawn a process inter-dependent with parent process.
3. 我差点自己手动实现了一把 [child_process](https://nodejs.org/api/child_process.html#child_process_class_childprocess) 这是个深坑，还好找到了现成的轮子。
4. 轮子的用法
   ```javascript
      serverOptions: {
        command: 'npm run start',
        port: 3000,
      },

   ```

5. 改良的用法 （为了复用build产物，节约cpu）
   ```javascript
      serverOptions: {
        command: `http-server build -P https://example.com -p 3000`,
    },
   ```

6. 终极改良（手动实现一个简单的带proxy的node server）
  ```javascript
      serverOptions: {
        command: `node server.js`,
    },
  ```


## 小结
* 我想一条路在前端走到黑的啊，这个不是我该看的啊喂。