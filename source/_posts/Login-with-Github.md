---
title: Login with Github
author: せいい
top: false
cover: false
toc: true
date: 2021-01-01 23:15:16
password:
summary: 通过github进行登入
tags:
  - OAuth
categories:
  - Backend
---

## 需求背景
* 通过第三方进行登入

## 流程
![](steps.png)

## 核心步骤
1. 获取Code
2. 用Code换AccessToken

## 具体步骤
1. 在 [GitHub](https://github.com/settings/applications/new) 上来创建 OAuth App
    * Authorization callback URL 需要把login换成ghcallback
    * 例如  `/users/login` -> `/users/ghcallback`
    ![](step1.png)
2. 根据github的[OAuth文档](https://docs.github.com/en/free-pro-team@latest/developers/apps/authorizing-oauth-apps)拼接请求链接
    * 建议使用encodeURIComponent() 拼接url

    ```javascript
    const url = 'https://github.com/login/oauth/authorize'
         + '?client_id=' + encodeURIComponent( 之前获取的id )
         + '&redirect_uri=' + encodeURIComponent( 授权成功后返回的地址 );         
    ```
3. 授权成功后，会在回调的url的查询参数里找到code  🎉撒花🎉
4. 通过axios发送post请求获取AccessToken  🎉撒花🎉
    * 步骤1获取的 `Client ID` & `Client secrets` 和步骤3获取的code作为参数向github请求数据
    ```javascript
    const {data} = await axios.post( 'https://github.com/login/oauth/access_token', params);
    ```
    ![](step2.png)
5. 通过AccessToken获取github的用户信息  🎉完结撒花🎉
    * 发送get请求获取用户信息

    ```javascript
    const user = await axios.get( 'https://api.github.com/user?access_token='+ AccessToken );
    ```


## 参考
* [方糖新全栈·React+Node必修课](https://study.163.com/course/courseMain.htm?courseId=1209581854)
* [github文档](https://docs.github.com/en/free-pro-team@latest/developers/apps/authorizing-oauth-apps)

## 写作耗时
* 3小时
