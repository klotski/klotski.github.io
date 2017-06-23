---
layout: default
title: 安装包管理工具
category: Linux
---

RPM

首先通过  rpm -q <关键字> 可以查询到rpm包的名字


然后 调用 rpm -e <包的名字> 删除特定rpm包


如果遇到依赖，无法删除，使用 rpm -e --nodeps <包的名字> 不检查依赖，直接删除rpm包


如果恰好有多个包叫同样的名字，使用 rpm -e --allmatches --nodeps <包的名字> 删除所有相同名字的包， 并忽略依赖

YUM

http://yum.baseurl.org/

