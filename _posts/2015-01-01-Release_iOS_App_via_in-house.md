---
layout: default
title: 以 in-house 方式发布ipa
category: MIS
---

**目标**
需要发布一个ipa放到网上，所有人（包括越狱及非越狱设备）可以直接通过链接下载安装，不需要通过AppStore，也不需要安装任何证书。要达到这个目标，就需要企业级开发账号（299$/year）。企业级开发账号的申请流程在这里就不细说，主要说一下In House ipa的发布流程。

**生成in-house证书**
1. 登录开发者中心
2. 生成appid
3. 生成证书
4. 生成描述文件

**打包ipa**
以Hbuilder为例

**发布ipa**
创建 ipa 同名的 plist文件，文件格式如下：
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

红色部分需要修改为你的工程实际内容。

然后把 .ipa 和 .plist 文件都上传到支持HTTPS协议的服务器，在网页源码里写入：
<a href="itms-services://?action=download-manifest&url=https://mydomain.com/apps/MyInHouseApp.plist" id="text">Install the In-House App</a>
在IOS设备iPhone 或 ipad上使用Safari浏览器打开https网址，点击上面的链接即可安装app了。
itms-services:这个是特殊的http协议,目前只有safari浏览器支持。

**可能遇到的问题**
如果应用在ios6和ios7设备上可以安装，但ios8设备上可以下载无法安装，可能是因为没有指定<full-size-image>和<display-image>段的图片地址。
http://blog.csdn.net/keshuiyun/article/details/45915261

存放plist文件的https服务器怎么办?

plist下载必须使用https协议，要么就花钱买个SSL证书给网站添加https支持，

不想花钱的可以使用github等托管plist文件，注意不要用可能会被墙的。


[iOS 消息推送 (Message) 证书设置指南](http://www.cnblogs.com/huangzizhu/p/4137571.html)


