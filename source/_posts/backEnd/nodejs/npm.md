---
title: npm使用方法
date: 2017-07-22
categories: [✬后端, NodeJS]
---

[NPM](https://www.npmjs.com/)是随同 NodeJS 一起安装的包管理工具，能解决 NodeJS 代码部署上的很多问题。

<!--more-->

## 查看信息

```bash
npm -v    #版本号
npm config ls #配置信息
```

## 安装模块

```bash
sudo npm install <Module Name> -g #全局安装
sudo npm install <Module Name>    #本地安装
sudo npm install <Module Name> -save #本地安装并保存到package.json
sudo npm install  #本地安装package.json中dependencies下的依赖包
```

### 全局安装

1. 将安装包下载到`/usr/local`下或者`node的安装目录`。
2. 可以直接在命令行里使用。

### 本地安装

1. 将安装包下载到`./node_modules`下（运行 npm 命令时所在的目录），如果没有`node_modules`目录，会在当前执行 npm 命令的目录下生成`node_modules`目录。
2. 可以通过`require()`来引入本地安装的包。

如果你希望具备两者功能，则需要在两个地方安装它或使用 npm link。

## 查看安装信息

```bash
sudo npm list -g #全局安装信息
sudo npm list    #本地安装信息
```

## 卸载模块

```bash
sudo npm uninstall <Module Name> -g #全局卸载
sudo npm uninstall <Module Name>    #本地卸载
```

## 更新模块

```bash
sudo npm update <Module Name> -g #全局更新
sudo npm update <Module Name>    #本地更新
```

## 发布模块

发布前需要在官网注册账号。

```bash
sudo npm init    #初始化
sudo npm login   #登陆账号
sudo npm publish --access public #发布
sudo npm unpublish <package>@<version> #撤销自己发布过的某个版本
```

## 使用淘宝镜像

淘宝 NPM 镜像官网：https://npm.taobao.org/

```bash
npm config set registry https://registry.npm.taobao.org/ #更换淘宝源
npm config set registry https://registry.npmjs.org/ #若要发布模块，需换回官方源
##或使用cnpm：
sudo npm install -g cnpm --registry=https://registry.npm.taobao.org
```
