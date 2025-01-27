---
abbrlink: ''
categories:
- - Hexo
date: '2025-01-27T14:25:01.155212+08:00'
tags:
- Hexo
title: Hexo博客部署与管理
updated: '2025-01-27T14:44:26.328+08:00'
---
# 安装环境

## Git

[Git - Download for Windows](https://git-scm.com/downloads/win)

![](https://image.kaoqy.me/25/1/IMG_5311.jpeg)

选择 `64-bit Git for Windows Setup`

##Nodejs

一路下一步即可

[Node.js - Download Node.js](https://nodejs.org/zh-cn/download/)

![](https://image.kaoqy.me/25/1/IMG_5312.jpeg)

选择 `Windows Installer (.msi)`

也是一路下一步即可

# 本地部署

找一个文件夹打开终端执行

```bat
npm install -g npm@latest
```

![](https://image.kaoqy.me/25/1/IMG_5313.jpeg)

接着执行，会在本地生成blog目录，里面存放的就是Hexo源码

```bat
npm install -g hexo-cli
hexo init blog
```

![](https://image.kaoqy.me/25/1/IMG_5314.jpeg)

## 安装主题

下载Hexo Fliud主题 - [下载链接](https://github.com/fluid-dev/hexo-theme-fluid/archive/refs/heads/master.zip)

将下载下来的压缩包解压的 `themes`文件夹中


![](https://image.kaoqy.me/25/1/IMG_5316.jpeg)

并将解压出来的文件夹重命名为 `fliud`

接着修改 `blog`目录中的 `config.yml`文件

```yaml
theme: fluid  # 指定主题

language: zh-CN  # 指定语言，会影响主题显示的语言，按需修改
```

# 推送源码

## 创建存储库

名称为 `Hexo`选择 `Private` ![](https://image.kaoqy.me/25/1/IMG_5318.jpeg)

## 添加 `SSH Key`

回到 `CMD`

执行命令，注意要改成你注册Github的邮箱

并且按两次回车

```bat
ssh-keygen -t rsa -C "你的邮箱"
```

![](https://image.kaoqy.me/25/1/IMG_5319.jpeg)

打开以下目录，复制 `id_rsa.pub`中的内容
![](https://image.kaoqy.me/25/1/IMG_5320.jpeg)

打开[SSH and GPG keys](https://github.com/settings/keys)

粘贴刚刚 `id_rsa.pub`里的内容并保存 ![](https://image.kaoqy.me/25/1/IMG_5321.jpeg)
