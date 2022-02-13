---
title: Use Mongodb with Docker
author: せいい
top: false
cover: false
toc: true
tags:
  - Docker
  - Mongodb
categories:
  - Backend
date: 2022-02-13 22:52:23
summary: 开始使用由docker跑起来的mongodb
---

## 背景
[搭建完mongodb](https://shengwei.innihon.com/post/start-mongodb-with-docker/)后还漏了几个步骤，不能在本地使用

## STEP
```bash
# 1. 进入容器内部
docker exec -it mongo bash

# 2. 下载vim
apt-get update
apt-get install vim

# 3. 修改配置文件
vim /etc/mongod.conf.orig

# bindIp: 127.0.0.1 -> bindIp: 0.0.0.0

```