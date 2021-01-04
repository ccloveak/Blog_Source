---
title: Two Scenarios with 'git rebase'
author: せいい
top: false
cover: false
toc: true
tags:
  - 工作经验
categories:
  - git
date: 2021-01-04 21:55:41
summary: 工作中的 'git rebase'
---

## 背景
* 新年上班第一天，本地master分支落后服务器master分支176个提交（我的同事好努力啊 ^_^ ）。
![](img0.png)
* 放假前工作有些不够专心，在一个分支上有很多个提交(才没有，平常也是一个分支有很多提交的)。
![](img1.png)

## 通过变基清理本地历史
1. 修改默认的编辑器 （强烈推荐 atom）
```bash
git config --global core.editor 'atom --wait'
```
2. 开始变基(从想合并的上一个提交开始)
```bash
git rebase -i ad23981
```
    * 操作前 ![](img2.png)
    * 操作后 ![](img4.png)  
* r s p是什么
![](img3.png)

3. 第一次变基完成 🎉撒花🎉

## 解决合并冲突
1. 不管3721上来直接:
```bash
git fetch
git pull --rebase origin master
```
2. 解决合并冲突

3. 要是已经清理过本地的话不存在步骤3
```bash
git rebase --continue
```
4. 暂存提交
```bash
git add.
git commit
```
5. 第二次变基完成 🎉撒花🎉
![](img5.png)
