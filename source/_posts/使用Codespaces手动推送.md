---
abbrlink: ''
categories:
- - Hexo
date: ''
tags:
- Hexo
- Github
title: 使用Codespaces手动推送
updated: '2025-01-02T20:55:15.379+08:00'
---
使用Qexo修改后，并不会推送静态文件

于是我搞了一个简单的推送方法

正在搞全自动Action

### 第一步

检查Hexo源码仓库的 `_config.yml`是否配置 `PAT`密钥 ![](https://raw.githubusercontent.com/kaoqy/Image/refs/heads/main/25/1/IMG_5019.jpeg)

```yaml
仓库连接 https://github.com/username/name
添加PAT 如https://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@github.com/username/name
```

### 第二步

在Hexo源码仓库创建Workspaces

### 第三步

更新Node.js至最新版

```bash
npm install -g npm@latest
```

![](https://raw.githubusercontent.com/kaoqy/Image/refs/heads/main/25/1/IMG_5020.jpeg)

### 第四步

安装Hexo

```bash
npm install -g hexo-cli
```

![](https://raw.githubusercontent.com/kaoqy/Image/refs/heads/main/25/1/IMG_5022.jpeg)

### 第五步

安装推送插件，并修复

```bash
npm install hexo-deployer-git --save
npm audit fix
```

![](https://raw.githubusercontent.com/kaoqy/Image/refs/heads/main/25/1/IMG_5023.jpeg)

### 第五步

输入推送命令将静态文件推送至Github仓库

```bash
hexo d
```

如果可以帮我写一个Actions，可以与我联系me@kamail.us.kg
