---
title: Ubuntu下Docker安装与使用
date: 2017-08-06
categories: [⚝系统, 虚拟化]
---

Docker 可以让开发者打包他们的应用以及依赖包到一个轻量级、可移植的容器中，然后发布到任何流行的 Linux 机器上，也可以实现虚拟化。
容器是完全使用沙箱机制，相互之间不会有任何接口（类似 iPhone 的 app）,更重要的是容器性能开销极低。

<!--more-->

## 1.下载安装包

```bash
cd /usr/local/     #进入/usr/local目录
sudo wget https://download.docker.com/linux/ubuntu/dists/xenial/pool/stable/amd64/docker-ce_17.03.2~ce-0~ubuntu-xenial_amd64.deb
```

## 2.运行安装

```bash
sudo apt-get install libltdl7 #安装libltdl7依赖包
sudo dpkg -i ./docker-ce_17.03.2~ce-0~ubuntu-xenial_amd64.deb #安装
sudo docker run hello-world #测试
```

## 3.卸载

```bash
sudo dpkg -r docker-ce ##卸载
```

## 4.国内镜像

[阿里云](https://cr.console.aliyun.com/#/accelerator)

```bash
sudo mkdir -p /etc/docker #docker的配置路径
sudo tee /etc/docker/daemon.json <<-'EOF'
{
  "registry-mirrors": ["https://xjw6ba2s.mirror.aliyuncs.com"]
}
EOF #写入配置文件
sudo systemctl daemon-reload #配置文件生效
sudo systemctl restart docker #重启
```
