---
layout: default
title: RobotFramework + Selenium2Library 典型问题
category: Software Testing
---

## 如何使用自定义的Profile

**Chrome:** [Using Create WebDriver Keyword](http://stackoverflow.com/questions/38226102/robot-framework-cannot-open-chrome-from-existing-chrome-profile)
```
${options}=         Evaluate    sys.modules['selenium.webdriver'].ChromeOptions()   sys, selenium.webdriver
Call Method         ${options}  add_argument                --user-data-dir\=/path/to/your/custom/profile
Create WebDriver    Chrome      chrome_options=${options}
```

以下 flag 可根据情况选用
```
--allow-running-insecure-content
--disable-web-security
--user-data-dir\=C:\\Users\\Mask\\AppData\\Local\\Google\\Chrome\\RobotFramework
--start-maximized
--disable-infobars
--incognito 
```
See also: http://peter.sh/experiments/chromium-command-line-switches/

Tip1: 
Windows中路径要用双反斜线，如
`--user-data-dir\=C:\\Users\\Mask\\AppData\\Local\\Google\\Chrome\\RobotFramework`

Tip2: 
将以上方法封装为 `Open Chrome` 后可放入 Suite Setup
`Run Keywords | Log | Launching browser... | AND | Open Chrome | AND | Set Browser Implicit Wait | 30 | AND | Log | Browser launched successfully`

Tip3:
禁用 Chrome 未正确关闭的提示，以下方式任选一尝试

-  Setting/Advanced, check/uncheck the box for "Continue running background apps when Google Chrome is closed" option.
-  Open `%UserProfile%\AppData\Local\Google\Chrome\User Data\Default\preferences`, find `"exit_type": "Crashed"`, then replace `Crashed` with `normal` like `"exit_type": "normal"`, save and relaunch Chrome.
-  Go to `chrome://flags/`, then click Enable on the link that writes: "Disable Better session restore"
-  `--incognito`

See also：https://sites.google.com/a/chromium.org/chromedriver/capabilities

**Firefox:** [Optional 'ff_profile_dir' is the path to the firefox profile dir.](http://robotframework.org/Selenium2Library/Selenium2Library.html#Open%20Browser)


## 用例运行失败后webdriver的进程不会结束

**Chrome:** 在 Test Suite 中导入 `OperatingSystem` 库，将以下方法封装为 `Close Chrome` 放入Suite Teardown
`Run Keywords | Log | Closing browser... | AND | Close Chrome | AND | Log | Browser closed successfully`

```
Close All Browsers		
${RunOutput}=           OperatingSystem.Run     taskkill /F /IM chromedriver.exe
Log                     ${RunOutput}=
```

**IE:** 同理
```
Close All Browsers	
${RunOutput}=           OperatingSystem.Run     taskkill /F /IM iedriver.exe
Log                     ${RunOutput}=
```

## 如何上传文件


## 如何下载文件



