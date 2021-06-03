---
title: E2E TEST
author: せいい
top: false
cover: false
toc: true
tags:
  - react
  - playwright
  - typescript
categories:
  - E2E
date: 2021-06-04 00:57:36
summary: 将E2E测试框架整合到当前项目
---

## 需求
* 项目需要导入e2e测试
* e2e测试整合到ci/cd pipeline

## 技术栈
* playwright
* typescript
* create-react-app
* node
* docker
* gitlab yml
* bash
* cross-env

## 大概步骤
* 在根目录新建e2e文件夹
* 新建个e2e测试项目 参考[playwright-jest-examples](https://github.com/playwright-community/playwright-jest-examples)
* 修改 e2e文件夹里的package.json文件，绑定主项目的 yarn start
* 启动服务器，进行e2e测试，关闭服务器
* 修改 .gitlab-ci.yml  集成到ci/cd

## 具体细节
* 通过 cross-env 修改启动e2e服务器时候的环境变量
* linux操作bash 重置e2e数据
* .gitlab-ci.yml 为了e2e 专门建个stage
* 使用docker 配置gitlab的runner ，有个docker in docker的配置
* node pm2相关
* npm script中&&和&
* 前端端口转发（通过环境变量选择转发的方向）
* jest相关配置

## 用上的的&没用上的代码
```bash
# 启动node的容器 并且直接可以输入命令
docker run --name e2e -exec node:14 tail -f /dev/null

# logs里找是否存在3000（端口）
pm2 logs e2e2 --lines 10 |grep 3000

# pm2启动前端服务器
pm2 start yarn --name e2e -- e2e:start

# 查看实时log
tail -f -2 ~/.pm2/logs/e2e-out.log

# 用bach访问一个容器内部
docker exec -it e2e bash

# 3000端口被占用情况，lsof需要下载 apt-get install lsop
lsof -i:3000

# 直接向一个地址发请求
curl --location --request GET 'https://example.com?token=exampletoken' \
--header 'TOKEN: これはTOKEN'

```

## 改进点
* 在playwright官方提供的docker镜像基础上再添加一些项目的依赖，减少ci/cd的时间

## 感受
* 满满的成就感