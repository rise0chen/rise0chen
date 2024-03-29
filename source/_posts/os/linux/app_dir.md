---
title: Linux软件应该安装到哪个目录？
date: 2016-01-29
categories: [⚝系统, Linux]
---

Linux 的软件安装目录是也是有讲究的，理解这一点，在对系统管理是有益的。

<!--more-->

`/usr`：系统级的目录，可以理解为 C:/Windows/，`/usr/lib`理解为 C:/Windows/System32。
`/usr/local`：用户级的程序目录，可以理解为 C:/Progrem Files/。用户自己编译的软件默认会安装到这个目录下。
`/opt`：用户级的程序目录，可以理解为 D:/Software，opt 有可选的意思，这里可以用于放置第三方大型软件（或游戏），当你不需要时，直接 rm -rf 掉即可。在硬盘容量不够时，也可将/opt 单独挂载到其他磁盘上使用。

源码放哪里？
`/usr/src`：系统级的源码目录。
`/usr/local/src`：用户级的源码目录。

-----------------翻译-------------------
`/opt`
Here’s where optional stuff is put. Trying out the latest Firefox beta? Install it to /opt where you can delete it without affecting other settings. Programs in here usually live inside a single folder whick contains all of their data, libraries, etc.
这里主要存放那些可选的程序。你想尝试最新的 firefox 测试版吗?那就装到/opt 目录下吧，这样，当你尝试完，想删掉 firefox 的时候，你就可 以直接删除它，而不影响系统其他任何设置。安装到/opt 目录下的程序，它所有的数据、库文件等等都是放在同个目录下面。
举个例子：刚才装的测试版 firefox，就可以装到/opt/firefox_beta 目录下，/opt/firefox_beta 目录下面就包含了运 行 firefox 所需要的所有文件、库、数据等等。要删除 firefox 的时候，你只需删除/opt/firefox_beta 目录即可，非常简单。

`/usr/local`
This is where most manually installed(ie. outside of your package manager) software goes. It has the same structure as /usr. It is a good idea to leave /usr to your package manager and put any custom scripts and things into /usr/local, since nothing important normally lives in /usr/local.
这里主要存放那些手动安装的软件，即不是通过“新立得”或 apt-get 安装的软件。它和/usr 目录具有相类似的目录结构。让软件包管理器来管理/usr 目录，而把自定义的脚本(scripts)放到/usr/local 目录下面，我想这应该是个不错的主意。
