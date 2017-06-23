---
layout: default
title: Redmine Installation (CentOS)
category: MIS
---

1. 安装RVM
http://rvm.io/

Before any other step install mpapis public key (might need gpg2) (see security)

gpg --keyserver hkp://keys.gnupg.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3

\curl -sSL https://get.rvm.io | bash -s stable

卸载RVM
$ rvm implode

更新RVM
http://rvm.io/rvm/upgrading

2. RVM 版本管理
rvm install ruby 1.9.3

ruby -v

如果还是1.8.7.

rvm use 1.9.3

 列出所有版本

rvm list

 设置默认的版本

rvm --default use x.x.x
2.




