---
title: CICD With Github Action
author: せいい
top: false
cover: false
toc: true
tags:
  - Docker
  - Github Action
  - AWS
categories:
  - インフラ
date: 2022-02-19 23:32:24
summary: 一个基本的完整的cicd流程
---

## 流程
* test -> build -> deploy

## 描述
1. test： 用react自带的测试框架做单体测试
2. build：使用docker构建项目镜像，推送到docker hub
3. deploy：在EC2里停止当前容器，拉取最新镜像，重新起一个容器

## 实际开发
1. 本地开发，本地服务器确认效果
2. 推送到github，自动部署到服务器
3. 可以通过公网访问页面

## 代码
[github repo](https://github.com/ccloveak/cicd-demo)

## 踩坑点
1. docker多阶段构建，减小image大小
2. docker使用Access Tokens登陆
3. github action直接访问EC2
4. EC2安装docker

## TODO
1. 在cicd过程中加入e2e测试
2. 通过AWS SSM进行部署

## 感受
1. 这些步骤其实之前都接触过，或者都已经写过博客，没有完整走一遍流程不知道自己哪里有欠缺。
2. 英语是真的重要，一些报错都是根据错误内容来调整的，特别是连接EC2这块。
3. 单纯前端上docker有点杀鸡用牛刀。不过都上了docker了，集成后端也是不难的。后端再连接云数据库，妥妥的cloud native。
4. github action，gitlab pipeline各有千秋吧，面向需求开发。