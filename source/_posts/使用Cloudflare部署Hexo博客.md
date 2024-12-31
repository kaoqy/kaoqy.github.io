---
abbrlink: ''
categories: []
date: '2024-11-08T05:12:32+08:00'
tags:
- Hexo
title: 使用Cloudflare部署Hexo博客
updated: '2024-12-31T23:13:07.342+08:00'
---
## 开始前，请保持一个良好的网络环境

### 一些链接

- [Hexo博客官网](https://hexo.io/)，可以查找更多主题。
- [GitHub](https://github.com/) 需要有一个GitHub账号，用来编辑你的代码。
- [Cloudflare](https://dash.cloudflare.com) 需要一个Cloudflare账号，将博客托管在上面
- [Bilibili](https://b23.tv/kqVIafj) 视频教程
- [抖音](https://v.douyin.com/iAAu6DLd/) 视频教程
- [YouTube](https://youtu.be/MdJWJ29dkgc)视频教程

### 创建新仓库

![](https://kaocdn.us.kg/image/Ep01/01.jpeg)
点击Code并开启codespaces(注⚠️:需要等一会)
![](https://kaocdn.us.kg/image/Ep01/02.jpeg)

### 更新Node.js

![](https://kaocdn.us.kg/image/Ep01/04.jpeg)

```bash
npm install -g npm@10.9.0
```

### 安装Hexo

#### 下载Hexo

![](https://kaocdn.us.kg/image/Ep01/05.jpeg)

```bash
npm install -g hexo-cli
```

#### 初始化

![](https://kaocdn.us.kg/image/Ep01/06.jpeg)

```bash
hexo init blog
```

#### 进入目录并安装依赖

![](https://kaocdn.us.kg/image/Ep01/07.jpeg)

```bash
cd blog
npm install
```

#### 选择并安装主题(注⚠️:这里的 `v1.9.8`要改成最新的版本号)

选择一个Hexo主题，例如 Fliud。
![](https://kaocdn.us.kg/image/Ep01/08.jpeg)

```bash
cd themes
wget https://github.com/fluid-dev/hexo-theme-fluid/archive/refs/tags/v1.9.8.zip
```

#### 解压

![](https://kaocdn.us.kg/image/Ep01/09.jpeg)

```bash
unzip v1.9.8.zip
```

#### 重命名

![](https://kaocdn.us.kg/image/Ep01/10.jpeg)

```bash
mv hexo-theme-fluid-1.9.8 fluid
```

#### 配置主题

![](https://kaocdn.us.kg/image/Ep01/11.jpeg)
修改Hexo根目录的 `_config.yml`，如

```yaml
theme: fluid
```

### 本地生成和预览

![](https://kaocdn.us.kg/image/Ep01/12.jpeg)

```bash
hexo clean
# 或者简写为 hexo cl
```

#### 生成静态文件：

![](https://kaocdn.us.kg/image/Ep01/13.jpeg)

```bash
hexo generate
# 或者简写为 hexo g
```

#### 启动本地服务器并预览

![](https://kaocdn.us.kg/image/Ep01/14.jpeg)

```bash
hexo server
# 或者简写为 hexo s
```

点击 `在浏览器中打开` 查看效果。

### 推送或部署到GitHub

确保已经在GitHub上创建了一个仓库。

#### 安装Hexo部署插件：

![](https://kaocdn.us.kg/image/Ep01/15.jpeg)

```bash
npm install hexo-deployer-git --save
```

#### 配置Hexo部署信息，在 `_config.yml`文件中的规范写法：

![](https://kaocdn.us.kg/image/Ep01/16.jpeg)

```yaml
deploy:
  type: git
  repo: https://github.com/你的用户名/你的最开始创建仓库名
  branch: main
```

如

```ymal
deploy:
  type: git
  repo: https://github.com/kaoqy/test
  branch: main
```

#### 推送到GitHub：

![](https://kaocdn.us.kg/https://raw.githubusercontent.com/kaoqy/img/refs/heads/main/18.jpeg)

```bash
hexo deploy
# 或者简写为 hexo d
```

##### 刷新一下Github仓库,就可以看到push上去的东西了

![](https://kaocdn.us.kg/https://raw.githubusercontent.com/kaoqy/img/refs/heads/main/19.jpeg)

### 使用免费容器进行部署

我用的是[Cloudflare](https://dash.cloudflare.com)

#### 创建Pages

![](https://kaocdn.us.kg/https://raw.githubusercontent.com/kaoqy/img/refs/heads/main/20.jpeg)

#### 用GitHub账户进行授权

![](https://kaocdn.us.kg/https://raw.githubusercontent.com/kaoqy/img/refs/heads/main/21.jpeg)

#### 选择你的GitHub仓库。

![](https://kaocdn.us.kg/https://raw.githubusercontent.com/kaoqy/img/refs/heads/main/22.jpeg)

#### 构建命令

![](https://kaocdn.us.kg/https://raw.githubusercontent.com/kaoqy/img/refs/heads/main/23.jpeg)

```bash
npm install -g hexo; hexo clean; hexo generate
```

其他的按预设就行了,可能要多部署几次
如果访问CF给你分配的域名可以加载出来
![](https://kaocdn.us.kg/https://raw.githubusercontent.com/kaoqy/img/refs/heads/main/24.jpeg)
就成功了

#### 绑定域名

由于CF的 `pages.dev`在国内并不好用，所以要绑定自己的一个域名
![](https://kaocdn.us.kg/https://raw.githubusercontent.com/kaoqy/img/refs/heads/main/25.jpeg)
点击自定义域(注⚠️:绑定的域名必须是已经在CF托管的)

### 总结

通过以上步骤，你应该已经成功安装并配置了Hexo博客，并且能轻易将其部署到互联网。
如有问题请联系

- email: support@kamail.us.kg
