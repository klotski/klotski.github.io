---
layout: default
title: Install Redmine on Windows
category: MIS
---

Redmine Version: 3.3.1
ROR: RailsInstaller 2.2 (include Ruby 2.2.4 + Rails 4.2)
DBMS: MySQL 5.7.13
OS: Windows Server 2008 R2 Enterprise

---
##  Manual Installation

#### Step 1 - Redmine application
Get the Redmine source code by downloading [a packaged release](http://www.redmine.org/releases/redmine-3.3.1.zip).

#### Step 2 - Create an empty database and accompanying user
**MySQL**
```sql
CREATE DATABASE redmine CHARACTER SET utf8;
GRANT ALL PRIVILEGES ON redmine.* TO 'redmine'@'localhost' IDENTIFIED BY 'my_password';
```

#### Step 3 - Database connection configuration
Copy config/database.yml.example to config/database.yml and edit this file in order to configure your database settings for "production" environment.

Example for a MySQL database using ruby 1.8 or jruby:
```
production:
  adapter: mysql
  database: redmine
  host: localhost
  username: redmine
  password: my_password
```
Example for a MySQL database using ruby 1.9 (adapter must be set to mysql2):
```
production:
  adapter: mysql2
  database: redmine
  host: localhost
  username: redmine
  password: my_password
```
If your server is not running on the standard port (3306), use this configuration instead:
```
production:
  adapter: mysql
  database: redmine
  host: localhost
  port: 3307
  username: redmine
  password: my_password
```




See also: http://www.redmine.org/projects/redmine/wiki/RedmineInstall

---

## Third-party Redmine Bundles
**BitNami Redmine Stack**

#### Step 1 - Download BitNamei Redmine
https://bitnami.com/redirect/to/131172/bitnami-redmine-3.3.1-0-windows-installer.exe)


#### Step 2 - Install

#### Step 3 - Configure Email
redmine@rochern.com
Rochern2513
smtp.exmail.qq.com


## Redmine Configuration
管理 - 配置 - 一般：主机名称，文本格式（Markdown）
管理 - 配置 - 显示：用户显示格式
管理 - 配置 - 认证：自动登录（30天），允许自注册（自动激活账号）
管理 - 配置 - 邮件通知：邮件发件人地址，邮件签名
管理 - 配置 - 版本：

Scm 命令不可用。
C:\Bitnami\redmine-3.3.1-0\apps\redmine\htdocs\config
configuration.yml

 开启 Bitnami Redmine 中 phpmyadmin的远程登录权限
 
 安装bitnami redmine之后，phpmyadmin只能在服务器上访问，如何开启远程访问权限呢。
方法如下：
远程到服务器上，进入 
盘符:\Bitnami\redmine-2.5.2-2\apps\phpmyadmin\conf
目录，打开 httpd-app.conf，把
<IfVersion >= 2.3>
Require local

修改为
<IfVersion >= 2.3>
Require all granted
