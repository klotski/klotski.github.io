---
layout: default
title: Building Enterprise Apps for In-House Distribution
category: MIS
---

**IMPORTANT**

The best way to find out helpful materials is to access [documentation hosted on the official website][official-doc].

The following is for personal use, I do not guarantee the accuracy, integrity and authority. 

## In-House 方式发布的优势

- 不需要通过 App Store，无需审核
- 通过链接（如二维码）下载安装

## 前提

- 企业开发者账号（299$/year）

## In-House 发布流程

### 1. Creating Additional Enterprise Distribution Certificates

1. 登录开发者中心
2. 生成appid
3. 生成证书
4. 生成描述文件

### 2. Exporting Your App In-House

这里通过Hbuilder云端打包生成.ipa文件

### 3. 发布ipa

创建 ipa 同名的 plist文件，文件格式如下：

```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
        <key>items</key>
        <array>
                <dict>
                        <key>assets</key>
                        <array>
                                <dict>
                                        <key>kind</key>
                                        <string>software-package</string>
                                        <key>url</key>
                                        <string>[INSERT URL HERE]</string>
                                </dict>
                        </array>
                        <key>metadata</key>
                        <dict>
                                <key>bundle-identifier</key>
                                <string>[INSERT BUNDLE ID HERE]</string>
                                <key>bundle-version</key>
                                <string>[INSERT VERSION HERE]</string>
                                <key>kind</key>
                                <string>software</string>
                                <key>title</key>
                                <string>[INSERT APP TITLE HERE]</string>
                        </dict>
                </dict>
        </array>
</dict>
</plist>
```

然后把 .ipa 和 .plist 文件都上传到支持HTTPS协议的服务器，在网页源码里写入：

<a href="itms-services://?action=download-manifest&url=https://mydomain.com/apps/MyInHouseApp.plist" id="text">Install the In-House App</a>

在iOS设备上使用Safari浏览器打开https网址，点击上面的链接即可安装app了。

itms-services是特殊的http协议,目前只有safari浏览器支持。


**存放plist文件的https服务器怎么办?**

plist下载必须使用https协议，要么就花钱买个SSL证书给网站添加https支持，或者使用github等托管plist文件。


See also:

- [Choosing a Membership1](https://developer.apple.com/support/compare-memberships/)
- [iOS 消息推送 (Message) 证书设置指南](http://www.cnblogs.com/huangzizhu/p/4137571.html)

[official-doc]: https://developer.apple.com/library/content/documentation/IDEs/Conceptual/AppDistributionGuide/DistributingEnterpriseProgramApps/DistributingEnterpriseProgramApps.html#//apple_ref/doc/uid/TP40012582-CH33-SW1
