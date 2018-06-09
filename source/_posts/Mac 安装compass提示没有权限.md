---
title: Mac 安装compass提示没有权限
date: 2018-06-09 20:56:30
tags: ruby/compass
categories: sass
---
### **Mac 安装compass提示没有权限**
- 我是想安装sass、compass的，sass 可以直接使用gem install sass安装成功（Mac自带ruby）；但是安装compass就不行了，在我输入了sudo gem install compass 之后还是提示没有权限写入/usr/bin目录，最后google了下才知道，原来苹果爸爸为了使OS X系统保证完整性，关闭部分目录的操作权限了(usr/local 目录除外)；
- 解决方法：首先切换当前用户环境，再正常安装就行了（系统版本:10.13.4）
1. sudo su   
2. sudo gem install -n /usr/local/bin compass