---
layout: default
title: 用批处理批量修改文件名
category: Tricks
---
1. 使用如下内容新建批处理文件。
2. 把需要批量修改的文件夹拖放到此bat文件上。
3. 按提示依次输入要替换的字符串和替换为的字符串即可。

```
@ECHO OFF
set batchName=批量重命名-替换文件或者文件夹的字符串
TITLE 批处理--%batchName%
rem [HEAD========================================================HEAD]
rem 名称：批量重命名
rem 概要：批量替换文件或者文件夹的字符串
rem 用法：
rem 1. 将需要批量重命名的文件所在的文件夹拖到该批处理文件上。
rem 2. 按提示输入要替换的字符串，然后按回车。
rem 3. 按提示输入想要替换为的字符串，然后按回车。
rem 
rem 考虑到多次操作，该批处理加了循环操作处理，可进行多次替换，而不
rem 需要多次拖文件夹。
rem [MID==========================================================MID]
rem [FOOT========================================================FOOT]
COLOR 0a
:main
set /a count=%count%+1

set /p oldStr=[请输入想要替换的字符串]
set /p newStr=[请输替换后的字符串]

for /f "tokens=*" %%a in (
'dir "%~1" /a /b'
) do (
SETLOCAL ENABLEDELAYEDEXPANSION
set "newFileName=%%~nxa"
set "newFileName=!newFileName:%oldStr%=%newStr%!"
ren "%~1\%%~nxa" "!newFileName!"
ENDLOCAL
)
ECHO.
echo 第 %count% 次替换已完成
ECHO.
goto :main
EXIT
```



