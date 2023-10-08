---
title: hexo使用教程
date: 2023-09-27 11:01:04
categories:
  - 教程
tags:
  - hexo
---
[Hexo](https://hexo.io/zh-cn/index.html)<br />1.安装

```tsx
 npm install -g hexo-cli
```

2.初始化

```tsx
hexo init
```

3.安装依赖

```tsx
npm i
```

4.常用命令

```json
"scripts": {
  "build": "hexo generate",//生成静态文件。
  "clean": "hexo clean",//清除缓存文件 (db.json) 和已生成的静态文件 (public)。
  "deploy": "hexo deploy",//部署网站。
  "server": "hexo server"//启动服务器。默认情况下，访问网址为： http://localhost:4000/。
},
```

5.启动服务<br />预览如下:<br />![image.png](https://cdn.nlark.com/yuque/0/2023/png/32689472/1695715234542-94e0a0d0-b7a9-4f69-8109-2b27e9ff8b33.png#averageHue=%23d0cdc2&clientId=u26d2356b-8686-4&from=paste&height=694&id=ppwLB&originHeight=867&originWidth=1740&originalType=binary&ratio=1.25&rotation=0&showTitle=false&size=691303&status=done&style=none&taskId=uc9674062-56a0-459e-b458-efa99655c3f&title=&width=1392)<br />6.新建文章

```jsx
hexo new [layout] title或 hexo n [layout] title
```

[GitHub+Hexo 搭建个人网站详细教程](https://zhuanlan.zhihu.com/p/26625249)<br />7.部署<br />![image.png](https://cdn.nlark.com/yuque/0/2023/png/32689472/1695783421947-1e1c3c62-d5c6-4c1a-9654-00070e4d3b90.png#averageHue=%232a2a24&clientId=ud4a7299d-9004-4&from=paste&height=124&id=OOb0j&originHeight=155&originWidth=345&originalType=binary&ratio=1.25&rotation=0&showTitle=false&size=10728&status=done&style=none&taskId=u2e284011-9b48-46f7-b3f1-b00f3ffe426&title=&width=276)<br />修改config文件,拉到最后,修改deploy设置<br />填写自己仓库的地址和分支

```
# Deployment
## Docs: https://hexo.io/docs/one-command-deployment
deploy:
type: git
repo: https://github.com/ilses1/ilses1.github.io.git
branch: master

```

```c
执行部署命令
hexo deploy //简写为 hexo d
```

8.更换主体<br />主题列表<br />[Themes](https://hexo.io/themes/)<br />以next主体为例<br />先拉代码或者npm

```c
$ git clone https://github.com/next-theme/hexo-theme-next themes/next
```

或者

```c
$ npm install hexo-theme-next
```

安装完后修改根目录下的config中的theme主体为next<br />_config.yml,也是拉到最后修改theme为next

```c
# Extensions
## Plugins: https://hexo.io/plugins/
## Themes: https://hexo.io/themes/
theme: next

```

然后执行以下命令

```c
hexo clean//清除缓存文件 (db.json) 和已生成的静态文件 (public)。
hexo g//生成静态文件。
hexo d////部署网站
```

预览如下<br />![image.png](https://cdn.nlark.com/yuque/0/2023/png/32689472/1695785182231-e4907cda-ed15-44f6-b723-4d06df2a1fbe.png#averageHue=%23fdfdfd&clientId=ud4a7299d-9004-4&from=paste&height=653&id=u4a32cf4a&originHeight=816&originWidth=1534&originalType=binary&ratio=1.25&rotation=0&showTitle=false&size=44858&status=done&style=none&taskId=uf0a83771-389e-4b37-b0a3-86a8dc8b4e3&title=&width=1227.2)

