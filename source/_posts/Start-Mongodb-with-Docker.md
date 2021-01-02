---
title: Start Mongodb with Docker
author: せいい
top: true
cover: false
toc: true
date: 2021-01-02 14:46:40
password:
summary: 解决mac不能通过brew安装mongodb的痛点
tags:
  - Docker Mongodb
categories:
  - Backend
---

## 背景
* mongodb改了共享协议，brew把mongodb给删了
* 直接安装mongodb需要踩很多坑
* 希望把时间花在具体业务上

## 准备工具
1. 终端
    * 敲命令的
2. docker
    * 跑mongodb的
3. MongoDB Compass
    * 看看mongodb有没有跑起来的

## 具体步骤
1. 拉取Mongo镜像
```bash
docker pull mongo
```

2. 创建MongoDB专用的文件夹
```bash
cd Documents
mkdir mongodb
cd mongodb
mkdir data backup
```

3. 启动MongoDB(两个冒号前面的换成自己的路径)
```bash
docker run --name mongo -p 27017:27017 -v /Users/zhangshengwei/Documents/mongodb/data:/data/db -v /Users/zhangshengwei/Documents/mongodb/backup:/data/backup -d mongo
```

4. 测试
* 用MongoDB Compass测试MongoDB是否正常工作
![](testconnect.png)
* 🎉完结撒花🎉
![](connectsuccess.png)

## 写作耗时
* 1小时
