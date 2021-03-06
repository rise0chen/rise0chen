---
title: linux搭建php运行环境
date: 2014-12-25
categories: [✬后端, PHP]
---

在 Ubuntu 中配置 PHP 开发环境。其中包括安装和配置 PHP 引擎、MySQL 数据库、Apache 服务器。

<!--more-->

## 安装 Apache 服务

```bash
sudo apt-get install apache2 #安装apache服务器
sudo vi /etc/apache2/apache2.conf #编辑配置文件
```

在配置文件最后面加入下面几行：

```apacheconf /etc/apache2/apache2.conf
AddType application/x-httpd-php .php .htm .html #添加文件类型支持
AddDefaultCharset UTF-8 #默认字符集 根据自己需要
#ServerName 127.0.0.1 #服务器地址，可更换为你的主机地址
DirectoryIndex index.html index.php #添加首页文，静态页面放在前边
```

服务器的访问目录在`/var/www`

## 安装 mysql

```bash
sudo apt-get install mysql-server #安装mysql
#安装的过程中会提示输入mysql的密码，输入两次，然后ok了
ps -ef | grep mysql #检查mysql服务
mysql -u root -p #输入数据库密码,进入数据库
```

## 安装 php5

```bash
sudo apt-get install php5 libapache2-mod-php5
sudo vi /etc/php5/apache2/php.ini #配置php.ini与apache相关的扩展
extension = mysql.so #去掉注释
extension = gd.so #添加
```

到这里就是基本上搭建完毕了。

##安装扩展包

```bash
sudo apt-get install php5-mysql
sudo apt-get install php5-cli
sudo apt-get install php5-curl
sudo apt-get install php5-gd
sudo apt-get install libapache2-mod-auth-mysql #安装Mysql模块

sudo /etc/init.d/mysql restart #重启mysql
sudo /etc/init.d/apache2 restart #重启apache
```

## 上传网站

在`/var/www`下面添加 php 文件，更改文件夹 www 下所有文件及文件夹的访问权限

```bash
sudo chmod -R 775 www
```

执行完成之后可以通过浏览器访问：http://127.0.0.1/
