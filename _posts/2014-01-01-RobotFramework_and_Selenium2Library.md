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



1. 安装Python
https://www.python.org/downloads/
需要安装2.6以上的2.x版本(如python-2.7.9.msi)，因为RIDE不支持 Python 3.
Python 2 官方只支持到2020年，Robot Framework 3 也支持Python 3。
安装完后设置环境变量，将Python的安装路径加入Path，如 “C:\Python27；C:\Python27\Scripts”。如果安装前已选中自动将python.exe的目录加入环境变量，刚无需单独再添加。

2. 安装Robot Framework
http://robotframework.org/
pip install robotframework
或者 robotframework-2.8.7.win32.exe

3. 安装wxPython
参见https://github.com/robotframework/RIDE/wiki/Installation-Instructions
最好安装wxPython2.8-win32-unicode-2.8.12.1-py27.exe，其他版本兼容性不太好

4. 安装RIDE
https://github.com/robotframework/RIDE/wiki
pip install robotframework-ride
或者robotframework-ride-1.3.win32.exe

5. 安装selenium2library
pip install robotframework-selenium2library

6. 解压chromedriver_win32.zip，放可执行文件放入Python根目录


cmd
ride.py
新建项目，选好路径好把demo.txt放入路径
重启ride
Library-Selenium2Library, save





*******************
Selenium
*******************
下载地址：https://pypi.python.org/pypi/selenium


如果是联网状态的话，可以直接在C:\Python27\Scripts  下输入命令安装：

C:\Python27\Scripts > pip install -U selenium

如果没联网，下载selenium 2.33.0 （目前的最新版本）

并解压把整个目录放到C:\Python27\Lib\site-packages 目录下。

*******************
安装Chrome driver
*******************
http://docs.seleniumhq.org/docs/03_webdriver.jsp#chrome-driver
下载后将解压的ChromeDriver.exe放置Python目录（C:\Python27\目录下）中就可以在脚本中直接调用了。

