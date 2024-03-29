---
title: Linux添加定时任务
date: 2015-06-03
categories: [⚝系统, Linux]
---

本文介绍如何使用 cron 实现定时任务。

<!--more-->

## 利用 cron 设置定时任务

```bash /etc/crontab
# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user  command
17 *    * * *   root    cd / &amp;&amp; run-parts --report /etc/cron.hourly
25 6    * * *   root    test -x /usr/sbin/anacron || ( cd / &amp;&amp; run-parts --report /etc/cron.daily )
47 6    * * 7   root    test -x /usr/sbin/anacron || ( cd / &amp;&amp; run-parts --report /etc/cron.weekly )
52 6    1 * *   root    test -x /usr/sbin/anacron || ( cd / &amp;&amp; run-parts --report /etc/cron.monthly )
#
#任务格式：分钟 小时 日期 月份 星期 执行用户 命令行
10 1    * * *   root    reboot
35 23   * * *   root    sh /opt/lampp/htdocs/tcp/mysql/bakMysql.sh
```

## 开机启动任务

```bash /etc/rc.local
#!/bin/sh
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

#/opt/lampp/bin/php /opt/lampp/htdocs/tool/tcp/test/server.php
/opt/lampp/xampp start
node /opt/lampp/htdocs/tcp/box.js > /opt/lampp/htdocs/tcp/log/box.log &
```
