---
layout: default
title: Red Hat Linux 用户基础
category: Notes
---
第1章 总览 
　1.1 登录 
　1.2 内核、程序和进程 
　1.3 查看文件系统 
　1.4 运行命令 
　1.5 管理终端 
　1.6 寻求帮助 
第2章 文件系统基础 
　2.1 文件系统导航 
　2.2 重要目录 
　2.3 文件管理 
　2.4 目录管理 
　2.5 文件名和文件名匹配 
　2.6 检查文件 
　2.7 文件编辑 
第3章 用户和组 
　3.1 Linux用户和/etc/passwd文件 
　3.2 Linux组和/etc/group文件 
　3.3 检查用户信息 
　3.4 改变身份 
第4章 文件所有者及权限 
　4.1 常规文件所有者及权限 
　4.2 改变文件权限：chmod命令 
　4.3 使用chgrp命令和chown命令改变文件所有者 
　4.4 目录所有者及权限 
　4.5 chmod命令回顾：八进制计数法 
　4.6 控制默认权限：umask 
第5章 Linux文件系统 
　5.1 文件详述 
　5.2 硬链接（hard links）和软链接（soft links） 
　5.3 目录与设备节点 
　5.4 磁盘、文件系统与挂载 
　5.5 使用locate和find命令查找文件 
　5.6 文件压缩：gzip和bipz2 
　5.7 文件归档：tar命令 
第6章 Bash Shell 
　6.1 Bash引言 
　6.2 命令列表和脚本 
　6.3 Bash变量 
　6.4 命令行替换 
　6.5 自定义Shell 
　6.6 获得Shell脚本和Shell初始化 
第7章 标准输入／输出和管道 
　7.1 标准输入和标准输出 
　7.2 标准错误 
　7.3 管道 
第8章 字符处理工具 
　8.1 文本编码及字数统计 
　8.2 搜索文本：grep 
　8.3 正则表达式介绍 
　8.4 排序命令：sort命令和uniq命令 
　8.5 提取和组合文本：cut命令和paste命令 
　8.6 追踪差异：diff命令 
　8.7 文本转换：tr命令 
　8.8 拼写检查：aspell命令 
　8.9 格式化文本（fmt）和文件分割（split） 
第9章 进程管理 
　9.1 进程 
　9.2 进程状态 
　9.3 进程调度：优先级（nice）和更改优先级（renice） 
　9.4 发送信号 
　9.5 作业控制 
　9.6 调度延迟的任务：at命令 
　9.7 调度周期任务：cron 
第10章 网络应用程序 
　10.1 TCP/IP联网简介 
　10.2 Linux打印 
　10.3 管理打印文件 
　10.4 电子邮件概述 
　10.5 Evolution MUA 
　10.6 网络诊断程序 
　10.7 基于终端的网络和 FTP 客户端程序 
　10.8 远程Shell命令 
第11章 补充材料 
　11.1 高级Shell脚本编程 
　11.2 RPM软件包管理器 
　11.3 使用YUM管理软件包 
　11.4 图形环境简介

---
本书所用系统版本为[RHEL](https://www.redhat.com/en/technologies/linux-platforms/enterprise-linux "Red Hat Enterprise Linux") 5
[RHCE](https://www.redhat.com/en/services/certification/rhce "Red Hat Certified Engineer")

---
[TOC]

---
## 第一章 总览

### 1.1 登录

登录方式：
- 虚拟控制台（Ctrl+Alt+F1 ~ F6）
- 图形界面（Ctrl+Alt+F7）【X xerver】
- 远程shell

退出：exit

who     列出当前登录的用户及其登录方式
:0      指的是X服务器本身；
pts/0   指的是在X服务器中打开的和一个终端

### 1.2 内核、程序和进程

Shell 是一个交互式进程，让用户指定要运行的其他进程

ps 列出从单个终端上启动的进程
ps aux 显示所在正在机器上运行的进程的详细列表

### 1.3 查看文件系统

ls 列出目录内容（list）
cat 检查文件内容 (concatenates)
用Shell命令行的`>`可以把命令的输出从终端重定向到文件

**文件引用方式**

 - 绝对引用：相对于根目录的文件引用
 - 相对引用：相对于当前工作目录的文件引用

### 1.4 运行命令

which   查找指定命令的目标文件

运行命令时，Shell 进程指示内核把指定的程序作为另一个进程分开执行，并将进程的输出（或更准确地说，标准输出流）写到终端。然后 Shell 暂停，等待命令的进程结束运行。一旦命令结束，Shell 会给出另一个提示符，等待下一个命令。

- 短命令行选项
- 长命令行选项

touch   更新指定文件上的时间戳

### 1.5 管理终端

reset   将终端设置恢复为正常状态
wc  行、词、字符计数

**Linux 终端控制组合组合键**
|组合键|符号名称|约定使用|
|---|---|---|
|Ctrl+C|SIGINT|非常规中断——终止前台进程|
|Ctrl+D|EOT|输入完成的正常信号|
|Ctrl+G|BEL|终端声效|
|Ctrl+H|BS|后退一格——删除前一个字符|
|Ctrl+J|LF|换行——与 Enter 键功能相同|
|Ctrl+L|FF|换页——使 bash 清屏，使其他基于屏幕的程序“刷新”当前屏幕|
|Ctrl+Q||解锁终端显示（见Ctrl+S）|
|Ctrl+S||锁住终端显示（使用Ctrl+Q解锁）|
|Ctrl+U|NAK|删除当前的行|
|Ctrl+Z|SIGSTOP|挂起前台进程，挂起的程序可用`fg`恢复|

**终端设备名称**
|名称|设备|使用|
|---|---|---|
|ttyn|虚拟控制台|使用 Ctrl+Alt+Fn 组合键访问|
|ttySn|串口端口设备|连接到串行端口上的调制解调器或 VT100 类型。UNIX 中的 ttyS0 等于 DOS 中的 COM1，ttyS1等于 DOS 中的 COM2，以此类推。|
|pts/n|伪终端|一个模拟终端，经常被 X 图形环境中的终端窗口或起始于网络的 Shell （如 telnet 和 ssh）使用。伪终端不能直接与物理设备相连。|
|:0|X 服务器|X 服务器并不是真正的终端。当用户使用 X 图形环境的登录管理器登录时，其终端经常被列为 X 服务器本身。|

### 1.6 寻求帮助

- 用法概要：用`--help` `-h` `-?`命令行选项调用命令时，大多数命令都会提供简洁的用法概要信息。
- Manual Page：更详细的参考信息可以使用`man`命令
- Info Page：很多更复杂的命令说明，使用`pinfo`命令
- LDP (Linux Documentation Project) Linux 文档项目提供大量与 Linux 有关的文档。

**man page 章节**
|章节|读者|主题|
|---|---|---|
|1|一般用户|命令|
|2|开发人|系统调用|
|3|开发人|库调用|
|4|管理员|设备文件|
|5|一般用户|文件格式|
|6|一般用户|游戏|
|7|一般用户|一般信息|
|8|管理员|管理员命令|


## 第6章 Bash Shell

~/.bashrc   初始化bash

**命令历史记录**
上、下箭头  快速浏览命令记录列表
左、右箭头  移动光标编辑当前命令
Enter       执行当前命令

**bash 历史记录替换**
|语法|替换|
|----|----|
|!!|前一个命令|
|!n|第n个命令|
|!-n|倒数第n个命令|
|!cmd|最后一个以cmd开头的命令|

**bash shell 命令历史记录变量**
|变量|默认值|作用|
|----|------|----|
|HISTFILE|~/.bash_history|退出时，命令历史记录会保存在该文件中；启动时，命令历史记录从该文件初始化|
|HISTFILESIZE|1000|启动时，文件 HISTFILE 将被截取到这个大小|
|HISTSIZE|1000|退出时，被写入文件 HISTFILE 中命令的最大数目|

**history 命令技巧**
Esc+. 和 Alt+.  恢复之前被键入的命令行的最后一个标记
Ctrl+R          之后键入的文本与之前键入的命令相匹配，即时显示命令，可在执行前编辑检索行
fc              打开默认编辑器（vi）把之前键入的命令作为文本进行整理，退出编辑器时（可能是编辑命令之后）新文本会立刻执行

**禁止命令历史记录**

1. 删除历史记录文件
`rm .bash_history`
2. 创建同名软链接，解析到/dev/null设备节点中
`ln -s /dev/null .bash_history`

可恢复当前shell中所用的命令，但是不会在shell会话之间保存命令记录。

### 6.2 

---
userid 用户ID
virtual console 虚拟控制台
Login Manager 登录管理器
terminal 终端
SSH (Secure Shell) 安全Shell
hostname 主机名
Command Line Interface 命令行界面
Process ID (PID) 进程ID
root directory 根目录
current working directory 当前工作目录
absolute    绝对
relative    相对
standard out    标准输出
redirect    重定向
argument    参数
usage   用法
Tab completion  Tab 补全
foreground  前台
Module      模块
















