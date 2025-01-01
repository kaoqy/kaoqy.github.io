---
abbrlink: ''
categories: []
date: '2025-01-01T18:00:16.462601+08:00'
tags: []
title: title
updated: '2025-01-01T18:01:35.602+08:00'
---
使用Qexo修改后，并不会推送静态文件

于是我搞了一个简单的推送方法

后面，再慢慢搞全自动Action

### 第一步

检查Hexo源码仓库的 `_config.yml`是否配置 `PAT`密钥 ![](https://raw.githubusercontent.com/kaoqy/Image/refs/heads/main/25/1/IMG_5019.jpeg)

格式

```yaml
仓库连接 https://github.com/username/name
添加PAT 如https://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@github.com/username/name
```
