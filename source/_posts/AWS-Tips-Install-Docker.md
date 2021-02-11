---
title: AWS Tips 'Install Docker'
author: せいい
top: false
cover: false
toc: true
tags:
  - AWS
  - docker
categories:
  - インフラ
date: 2021-02-10 02:04:53
summary: Linux install docker.
---

## 背景
* 装个docker就不用出了问题新建实例了

## 操作
1. 更新实例上已安装的程序包和程序包缓存
```bash
sudo yum update -y
```
2. 安装最新的 Docker Engine 程序包
```bash
sudo yum install docker
```
3. 启动 Docker 服务
```bash
sudo service docker start
```
4. 将 root 添加到 docker 组
```bash
sudo usermod -a -G docker root
```
5. 解决 `WARNING: bridge-nf-call-iptables is disabled`
```bash
vim /etc/sysctl.conf

# sysctl.conf
net.bridge.bridge-nf-call-ip6tables = 1
net.bridge.bridge-nf-call-iptables = 1

sysctl -p
```

## EC2 type
* Amazon Linux 2 AMI (HVM), SSD Volume Type 

## 参考
* [aws](https://docs.aws.amazon.com/zh_cn/AmazonECS/latest/developerguide/docker-basics.html)
* [aliyun](https://developer.aliyun.com/article/278801)
