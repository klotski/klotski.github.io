---
layout: default
title: RobotFramework+Selenium2Library
category: Software Testing
---

完整的安装方式请参考 RobotFramework 官方文档：https://github.com/robotframework/robotframework/blob/master/INSTALL.rst#introduction
以下只记录个人最近一次的安装：
Operating System: Windows 8.1 64bit
1. 安装 Python
- 下载 Python for Windows 最新版：https://www.python.org/ftp/python/3.5.1/python-3.5.1-amd64.exe
- 以管理员权限运行安装文件，并安装给所有用户。
- 安装时选择将python.exe的目录加入环境变量Path，或安装完后设置环境变量

C:\Program Files\Python35;C:\Program Files\Python35\Scripts

See also：https://www.python.org/
2. 安装 RobotFramework
- 管理员权限运行命令提示符

pip install robotframework

See also: http://robotframework.org/
3. 安装编辑器
Vim:
https://github.com/mfukar/robotframework-vim

注：如果编辑器用RIDE，Python只能安装2.6以上的2.x版本，因为RIDE不支持 Python 3。
参见https://github.com/robotframework/RIDE/wiki/Installation-Instructions
还有https://github.com/robotframework/RIDE/issues/1568
- 安装wxPython
最好安装wxPython2.8-win32-unicode-2.8.12.1-py27.exe，其他版本兼容性不太好
- 安装RIDE
- 安装RIDE
管理员权限运行命令提示符

pip install robotframework-ride

4. 安装selenium2library
https://github.com/robotframework/Selenium2Library
管理员权限运行命令提示符

pip install robotframework-selenium2library

https://github.com/robotframework/Selenium2Library/issues/573
暂时还不支持Python 3，安装会报错。
5. 安装 Chrome Driver
http://docs.seleniumhq.org/docs/03_webdriver.jsp#chrome-driver
下载后将解压的ChromeDriver.exe放置Python目录中就可以在脚本中直接调用了。




