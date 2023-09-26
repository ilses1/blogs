---
title: first
date: 2023-09-26 16:25:06
tags:
---



Hexo
Hexo is a fast, simple & powerful blog framework powered by Node.js.
Hexo

1.安装

1
 npm install -g hexo-cli

2.初始化

1
hexo init

3.安装依赖

1
npm i

4.常用命令

1
2
3
4
5
6
"scripts": {
  "build": "hexo generate",//生成静态文件。
  "clean": "hexo clean",//清除缓存文件 (db.json) 和已生成的静态文件 (public)。
  "deploy": "hexo deploy",//部署网站。
  "server": "hexo server"//启动服务器。默认情况下，访问网址为： http://localhost:4000/。
},

5.启动服务
预览如下:
﻿
image.png
﻿
6.新建文章

1
hexo new [layout] title或 hexo n [layout] title

