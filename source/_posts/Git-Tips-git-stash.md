---
title: Git Tips 'git stash'
author: せいい
top: false
cover: false
toc: true
tags:
  - 工作经验
categories:
  - git
date: 2021-01-14 23:12:28
summary: 最低限度的'git stash'
---

## 背景
* 开始review代码，需要频繁切分支
* 当前的变更不想提交

## 操作流程
1. `git stash`
2. `git checkout 其他分支`
3. 做一些事情 `yarn storybook` , `yarn test` 等等
4. `git checkout 之前工作分支`
5. `git stash pop`

## 小结
* git真是啥功能都有 🎉
* 'git stash' 还有其他魔法操作，不过对我目前来说，现在这样够用了。
    * 我堕落了，我丧失了求知欲。。。
