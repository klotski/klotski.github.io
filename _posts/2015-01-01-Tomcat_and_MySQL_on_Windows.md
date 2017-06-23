---
layout: default
title: Tomcat + MySQL 部署（Windows）
category: MIS
---

下载JDK、Tomcat、MySQL
### 1. 安装JDK
设置环境变量
- 新建 JAVA_HOME 变量，值填写JDK的安装目录（比如 C:\Program Files\Java\jdk1.8.0_45)
- 编辑 Path 变量，值增加 `%JAVA_HOME%\bin;%JAVA_HOME%\jre\bin;`
- 新建 CLASSPATH 变量，值填写 `.;%JAVA_HOME%\lib;%JAVA_HOME%\lib\tools.jar`
运行cmd 输入 `java -version`，若显示版本信息则说明安装和配置成功。
### 2. 安装Tomcat
配置（端口、服务、数据库、日志路径、图片路径等）
设置为后台服务自动启动
- cmd 进入tomcat安装路径的bin目录。
-执行 service.bat install，出现 The service 'tomcat7' has been installed 说明设置服务成功。
-运行 service.msc（或依次打开控制面板-管理工具-服务），找到Apache Tomcat的服务，并修改启动类型为“自动”。（如安装多个服务，可将service.bat里的 SERVICE_NAME 改为不同的值）
### 3. 安装MySQL
解压安装文件
设置环境变量Path，值增加MySQL的bin目录，如 C:\GZ\MySQL-5.7.13\bin
修改配置文件my.ini：
[mysqld]
basedir=C:\Program Files\MySQL\MySQL Server 5.6（mysql所在目录）
datadir=C:\Program Files\MySQL\MySQL Server 5.6\data （mysql所在目录\data）
安装MySQL服务：
- 以管理员身份运行cmd
- 进入MySQL的bin目录
- 输入mysqld -install（也可以指定配置文件的地址，如：mysqld -install MySQL --defaults-file="D:\software\mysql5.7.12\my-default.ini"，"MySQL"为显示的服务名）
初始化（从5.7.7开始，windows下的安装包不包含data目录，在启动服务之前需要先初始化数据）：
-mysqld –initialize(或mysqld --initialize --user=mysql --console)
修改root密码初始化会为root生成一个随机的密码，从data目录下的.err文件中可以看到）(*特别提醒注意的一点是，新版的mysql数据库下的user表中已经没有Password字段了而是将加密后的用户密码存储于authentication_string字段)
-mysql>mysql -u root -p
-mysql>alter user 'root'@'localhost' identified by 'Rochern';
-mysql>flush privileges;
新建数据库
-mysql>create database hw_score;
新建用户并授权用户拥有指定数据库的所有权限：
-mysql>CREATE USER 'gztest'@'%' IDENTIFIED BY 'GZ.test';
-mysql>grant all privileges on hw_score.* to 'gztest'@'%' identified by 'GZ.test';(格式：grant 权限 on 数据库.* to 用户名@登录主机 identified by "密码";　)
- mysql>flush privileges;//刷新系统权限表
其他常用命令
-启动 net start mysql
-停止 net stop mysql
-移除服务 mysqld -remove（如果服务名不是MySQL需要指定服务名，如mysqld -remove MySQL-Server）





