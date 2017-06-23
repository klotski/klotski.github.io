---
layout: default
title: 创建指定大小的文件
category: Tricks
---

测试中，有时会遇到需要特殊大小的文件的场景，使用下面的方法可以快速创建指定大小的文件。

####Windows
命令：fsutil file createnew <filename> <length>
`fsutil file createnew C:\testfile.txt 1024`
创建一个1kb大小的文件
注意：fsutil需要在管理员权限下运行。
####Linux
命令：dd
`# dd if=/dev/zero of=50M.file bs=1M count=50`
在当前目录下生成一个50M的文件
See also: http://rubyer.me/blog/196/
