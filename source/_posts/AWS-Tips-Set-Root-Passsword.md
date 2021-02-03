---
title: AWS Tips 'Set Root Passsword'
author: せいい
top: false
cover: false
toc: true
tags:
  - AWS
categories:
  - Backend
date: 2021-02-04 00:27:49
summary: 设置aws的root密码
---

## 背景
* 通过 `*.pem` 登录aws ec2的时候，默认的不是root用户

## 操作
* 为root用户创建密码
  ```bash
  sudo passwd root
  ```

## 小结
* 有了root就能想干嘛干嘛了
  
