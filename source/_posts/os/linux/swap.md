---
title: 添加swap分区
date: 2019-08-11
categories: [⚝系统, Linux]
---

## swap 分区介绍

Linux 将物理内存分为内存段的部分被称作“页面”。交换是指内存页面被复制到预先设定好的硬盘空间(叫做交换空间)的过程，目的是释放用于页面的内存。物理内存和交换空间的总大小是可用的虚拟内存的总量。  
交换空间通常是一个磁盘分区（此分区在安装操作系统时，系统通常会默认划分出一段空间用于交换分区，默认将交换空间的大小设定为内存的 1 倍到 2 倍），也可以是一个文件。

<!--more-->

## 创建 swap 分区

```bash
# 新建 swap 文件
sudo dd if=/dev/zero of=/mnt/swap bs=1M count=2048
sudo chmod 0600 /mnt/swap
# 把swap文件做成 swap 分区
sudo mkswap /mnt/swap
# 启用交换分区的交换功能
sudo swapon /mnt/swap
# 查看启用的 swap 分区
swapon -s
# 查看 swappiness
cat /proc/sys/vm/swappiness
# 查看内存占用情况
free -m
```

## 开机自动加载 swap 分区

```bash /etc/fstab
/mnt/swap  swap  swap  defaults  0  0
```

## 开机设置 swappiness

```bash /etc/sysctl.conf
vm.swappiness=40
```
