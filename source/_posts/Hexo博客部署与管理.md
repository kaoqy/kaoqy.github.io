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
