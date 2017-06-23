---
layout: default
title: 按键映射（Caps Lock -> Ctrl）
category: Tricks
---
## Windows - 修改注册表
在注册表的`HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Keyboard Layout\`下新建一个二进制值项`Scancode Map`，然后修改二进制值，在二进制编辑对话框中，输入：

     0000: 00 00 00 00 00 00 00 00
     0008: 03 00 00 00 1D 00 3A 00
     0010: 00 00 00 00
     
选择OK关闭对话框，退出注册表编辑器，注销或重启计算机。

**[项目格式]**
以16进制表示，分为五个部分，每个逗号之间都为一个字节。
"Scancode Map" = 00,00,00,00,00,00,00,00,   02,00,00,00,   01,00, 02,00,    00,00,00,00 

8个字节。 这是版本信息号。照例写就好。
4个字节。 这是映射键的总数。按照二进制的读写规则，低位在左，高位在右。02 00 00 00 这个数实际就是：00 00 00 02 。从 02 开始，一个映射键是 02 ，两个是03 ，依次递加，十个是 0B 。
2个字节。 表示替换后按键的”扫描码“。如：ESC 键的扫描码是 01 ，所以就表示 01 00 。再如 左Ctrl键扫描码是 1D 00, 而右Ctrl键是 1D E0 。
2个字节。 表示原按键的”扫描码“。格式同上。
以四个 00 结束。
 
**[示例]**
1.屏蔽左右WIN两个键
  `"Scancode Map"=00,00,00,00,00,00,00,00,03,00,00,00,00,00,5B,E0,00,00,5C,E0,00,00,00,00`
  `"Scancode Map"=00,00,00,00,00,00,00,00,02,00,00,00,38,00,1D,00,00,00,00,00`

## Linux - xmodmap
在linux中，可以使用xmodmap工具。在用户主目录新建一个名为.xmodmap的文件，向该文件加入下列内容：
```
!
! Swap Caps_Lock and Control_L
!
remove Lock = Caps_Lock
remove Control = Control_L
keysym Control_L = Caps_Lock
keysym Caps_Lock = Control_L
add Lock = Caps_Lock
add Control = Control_L
```
保存，再向 ~/.bash_profile 文件加入一行：
`xmodmap ~/.xmodmap`
http://blog.csdn.net/robertsong2004/article/details/36439597

**See also:**
[Keyboard scancodes](http://www.win.tue.nl/~aeb/linux/kbd/scancodes.html): written by Andries Brouwer
 
