---
title: 如何解压asar文件(electron的打包二进制文件)
date: 2023-10-10 15:28:57
categories:
  - electron
tags:
  - electron
  - 解压
---


npm i asar

```powershell
$ npm install -g asar
$ #解压缩asar文件
$ #asar extract 压缩文件 解压目录
$ asar extract app.asar ./ap
$ #asar pack 压缩文件夹 压缩路径含文件名
$ asap pack ./app app.asar
```

