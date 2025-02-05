---
abbrlink: ''
categories:
- - Hexo
date: '2025-01-27T14:25:01.155212+08:00'
tags:
- Hexo
title: Hexo博客部署与管理
index_img: https://cdn1.kaoqy.me/article/Hexo.jpeg
updated: '2025-01-27T14:44:26.328+08:00'
---
# 安装环境

## Git

[Git - Download for Windows](https://git-scm.com/downloads/win)

![](https://cdn4.kaoqy.me/25/1/IMG_5311.jpeg)

选择 `64-bit Git for Windows Setup`

## Nodejs

一路下一步即可

[Node.js - Download Node.js](https://nodejs.org/zh-cn/download/)

![](https://cdn4.kaoqy.me/25/1/IMG_5312.jpeg)

选择 `Windows Installer (.msi)`

也是一路下一步即可

# 本地部署

## 安装Hexo

找一个文件夹打开终端执行

```bat
npm install -g npm@latest
```

![](https://cdn4.kaoqy.me/25/1/IMG_5313.jpeg)

接着执行，会在本地生成blog目录，里面存放的就是Hexo源码

```bat
npm install -g hexo-cli
hexo init blog
```

![](https://cdn4.kaoqy.me/25/1/IMG_5314.jpeg)

## 安装主题

下载Hexo Fliud主题 - [下载链接](https://github.com/fluid-dev/hexo-theme-fluid/archive/refs/heads/master.zip)

将下载下来的压缩包解压的 `themes`文件夹中


![](https://cdn4.kaoqy.me/25/1/IMG_5316.jpeg)

并将解压出来的文件夹重命名为 `fliud`

接着修改 `blog`目录中的 `config.yml`文件

```yaml
theme: fluid  # 指定主题

language: zh-CN  # 指定语言，会影响主题显示的语言，按需修改
```

# 推送源码

## 创建存储库

名称为 `Hexo`选择 `Private` ![](https://cdn4.kaoqy.me/25/1/IMG_5318.jpeg)

## 添加 `SSH Key`

回到 `CMD`

执行命令，注意要改成你注册Github的邮箱

并且按两次回车

```bat
ssh-keygen -t rsa -C "你的邮箱"
```

![](https://cdn4.kaoqy.me/25/1/IMG_5319.jpeg)

打开以下目录，复制 `id_rsa.pub`中的内容
![](https://cdn4.kaoqy.me/25/1/IMG_5320.jpeg)

打开[SSH and GPG keys](https://github.com/settings/keys)

粘贴刚刚 `id_rsa.pub`里的内容并保存 ![](https://cdn4.kaoqy.me/25/1/IMG_5321.jpeg)

## 本地创建存储库

```bat
git init
git add . 
```

![](https://cdn4.kaoqy.me/25/1/IMG_5322.jpeg)

我这里出现了报错，不过执行下面命令的时候，发现添加成功了

可以使用

```bat
git status
```

查看是否添加成功

## 推送至远程仓库

```bat
git remote add origin https://github.com/kaoquanyang123/Hexo.git
```

如果你在创建仓库时勾选创建了 `README.md`

那么你需要执行

```bat
git pull --rebase origin main
```

接着执行

```bat
git push -u origin main
```

# 前端部署

## fork项目

[Qexo项目地址](https://github.com/Qexo/Qexo)
将此项目fork到自己仓库

## 配置数据库

### 创建数据库

[TiDB数据库](https://tidbcloud.com) 用于Qexo连接

![](https://cdn4.kaoqy.me/25/1/IMG_5013.jpeg)

选择Serverless，有免费的5GB存储

### 修改数据库

点击右上角Connnet并点击Generate Password创建密码 ![](https://cdn4.kaoqy.me/25/1/IMG_5016.jpeg)

会获得下图的信息，备用

## 搭建前端

打开[Vercel](https://vercel.com)，点击 `Add New...`并且选择 `Project`

选择刚刚fork下来的仓库点击 `Import`,选择 `Environment Variables`

添加5个环境变量(对应的是上图的信息)

![](https://cdn4.kaoqy.me/25/1/IMG_5015.jpeg)

```json
MYSQL_HOST | MySQL数据库连接地址 |
MYSQL_PORT | MySQL数据库通信端口，默认应填写3306 |
MYSQL_USER | MySQL数据库用户名 |
MYSQL_NAME | MySQL数据库名 |
MYSQL_PASSWORD | MySQL数据库密码 |
```

点击Deploy

