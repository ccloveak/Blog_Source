---
title: Frontend Permissions System
author: せいい
top: false
cover: false
toc: true
tags:
  - React
categories:
  - Frontend
date: 2021-11-18 23:25:07
summary: 前端权限系统备忘
---

## 背景
* 项目分大小，权限系统总共就这些东西
* 没想到从スマカン出来短短两个礼拜又从头到脚做了一遍前端权限
* 温故知新，下次再做权限相关的课题速度更快

## 逻辑
1. 主要依赖3个表 user，role，feature（功能级别的颗粒读）
2. 通过role表管理 某个user可以使用哪些features

## 字段
```typescript
interface UserInfo {
    id: string;
    name: string;
    roleId: string;
} 

interface Role {
    id: string;
    name: string;
} 

interface Feature {
    features: string[]
    roles: Role[]
}

```

## api需求
* 向后端发请求的需求（从这部分切入到后端开发应该是个不错的选择）

```typescript
// 获取用户
{
    get: {
        '/api/users', params;//params是检索条件
    }
    response: UserInfo[]
}
// 新增用户
{
    post: {
        '/api/users', UserInfo;
    }
    response: UserInfo
}

// 删除用户
{
    delete: {
        `/api/users/${id}`;
    }
    response: id
}

// 编辑用户
{
    put: {
        `/api/users/${id}`, UserInfo;
    }
    response: UserInfo
}

// 获取role
{
    get: {
        '/api/roles', params;//params是检索条件
    }
    response: Role[]
}
// 新增role
{
    post: {
        '/api/roles', roleName;
    }
    response: Role
}

// 删除role
{
    delete: {
        `/api/roles/${id}`;
    }
    response: id
}

// 编辑role
{
    put: {
        `/api/roles/${id}`, Role;
    }
    response: Role
}

// 这部分由后端控制，不需要新建，不能够删除
// 获取feature
{
    get: {
        '/api/features', 
    }
    response: Feature
}

// 编辑feature 相当于新建了一套对应关系
{
    put: {
        `/api/features/`, params;// 一套新的对应关系
    }
    response: 200
}

```

## 下一步
1. 前端在操作资源的时候还需要注意防抖
2. 用户登陆的时候根据roleId获取feature，存到context里
3. 访问资源，点击按钮根据context里的权限进行判断

## 小结
TODO：用 后端express 前端next 服务器nginx 数据库 mongodb 写个跟权限控制相关的demo
