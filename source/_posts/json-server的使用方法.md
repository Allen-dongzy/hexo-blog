---
title: json-server的使用方法
top_img: images/top-img.jpg
cover: images/top-img.jpg
date: 2021-08-23 17:42:17
tags:
  - npm插件
  - json-server
categories:
  - [教程, npm插件, json-server]
description: 使用json-server在本地开启mock数据库，可以随心所欲使用RESTful风格api
---

## 引入

**yarn**

```
// 添加json-server
yarn add json-server --dev
```

**npm**

```
// 添加json-server
npm install json-server --save-dev
```

## 添加 json 本地数据库

```
// 这里的users可以是任意api字段，文件夹也可以是任意的(根目录也可以)
echo {\"users\":[]}> json-server __json_server_mock__/db.json
```

**此时项目根目录会出现 `json_server_mock`文件夹，里面有 `db.json`，内容是 `users` 列表。**

## 配置 package.json 文件

```
"scripts": {
  "json-server": "json-server __json_server_mock__/db.json --watch"
}
```

**这样使用 `yarn json-server` 就可以启动本地服务了**

## 使用

- 访问`http://localhost:3000/user`或是使用`GET`来请求可以看到本地服务器返回的结果
- 使用 POST 请求`http://localhost:3000/user`并携带`json`格式的内容(`{"name":"Rose"}`)可以新增用户
- 使用 PATCH 请求`http://localhost:3000/user/${id}`并携带`json`格式的内容(`{"name":"Tom"}`)可以修改用户
- 使用 DELETE 请求`http://localhost:3000/user/${id}`可以删除用户
