---
layout: default
title: File Transmission
category: Linux
---

**Option 1 FTP**
其中一台 Linux 安装 FTP Server，这样可以另外一台使用ftp的client程序来进行文件的拷贝；

**Option 2 Samba**

采用samba服务，类似Windows文件复制的方式来操作，比较简洁方便；

**Option 3**

利用scp命令来进行文件拷贝。

如果存放路径中有空格，用双引号引起来

**local 传到 remote**      scp     文件名1       远程用户名@IP地址:文件名2
**remote 传到 local**        scp    远程用户名@IP地址:文件名1       文件名2

假设多台路由器某几台在一个局域网内，另几台在另一个局域网中，通过公网连接。中间有路由器。

内网之间复制直接使用scp命令，比如1号到2号，或者1号到3号都可以

> scp /tmp/test.txt root@remote_server_ip:/tmp/

这条命令只能将文件复制到 remote_server（路由器）上。

如果到远程的局域网，比如3号机往1、2、4、5，或者1、2往4、5，就需要在路由器中设置端口映射。

比如将路由器的12345端口映射到内网1号机的22端口，在上条命令中加 -P（大写）12345就可以将文件复制到1号机上了。

> scp /tmp/test.txt root@remote_server_ip:/tmp/ -P 12345

将远程机的文件复制到本地方法一样，把文件顺序颠倒一下就行。
