---
title: AWS Tips 'ssh config'
author: せいい
top: false
cover: false
toc: true
tags:
  - AWS
categories:
  - インフラ
date: 2021-02-08 02:17:54
summary: 通过配置ssh直接连接到aws
---

## 需求
* 人为降低连接aws的复杂的
* 之前连接aws ` ssh -i "aws.pem" ec2-user@ec2-54-178-64-65.ap-northeast-1.compute.amazonaws.com`

## 具体操作
* 在 ~/.ssh下创建config
```bash
#  ~/.ssh/config
Host aws
    HostName 这里是ip或者dns
    User ec2-user
    Port 22
    IdentityFile ~/.ssh/aws.pem
    ServerAliveInterval 60
```

## 效果
* 目前连接aws `ssh aws`
