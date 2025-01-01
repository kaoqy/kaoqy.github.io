---
abbrlink: ''
categories:
- - Hexo
date: '2025-01-01T12:23:16.664638+08:00'
tags:
- Hexo
title: 使用Vercel部署Qexo管理Hexo
updated: '2025-01-01T17:32:53.061+08:00'
---
# 前端部署

## fork项目

[Qexo项目地址](https://github.com/Qexo/Qexo)
将此项目fork到自己仓库

## 配置数据库

### 创建数据库

[TiDB数据库](https://tidbcloud.com) 用于Qexo连接

 ![](https://raw.githubusercontent.com/kaoqy/Image/refs/heads/main/25/1/IMG_5013.jpeg)

选择Serverless，有免费的5GB存储

### 修改数据库

点击右上角Connnet并点击Generate Password创建密码 ![](https://raw.githubusercontent.com/kaoqy/Image/refs/heads/main/25/1/IMG_5016.jpeg)

会获得下图的信息，备用

## 搭建前端

打开[Vercel](https://vercel.com)，点击 `Add New...`并且选择 `Project`

选择刚刚fork下来的仓库点击 `Import`,选择 `Environment Variables`

添加5个环境变量(对应的是上图的信息)

![](https://raw.githubusercontent.com/kaoqy/Image/refs/heads/main/25/1/IMG_5015.jpeg)

```json
MYSQL_HOST | MySQL数据库连接地址 |
MYSQL_PORT | MySQL数据库通信端口，默认应填写3306 |
MYSQL_USER | MySQL数据库用户名 |
MYSQL_NAME | MySQL数据库名 |
MYSQL_PASSWORD | MySQL数据库密码 |
```

点击Deploy
