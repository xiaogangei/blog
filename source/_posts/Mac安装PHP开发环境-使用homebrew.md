---
title: Mac安装PHP开发环境(使用homebrew)
name: XiaoGang
date: 2020-12-11 12:30:49
tags:
  -Mac
  -PHP
categories: [Mac]
---
## 一、安装Nginx
### 1.1 安装命令
```
brew install nginx
```
### 1.2 设置文件权限
```
sudo chown root:wheel /usr/local/opt/nginx/bin/nginx
sudo chmod u+s /usr/local/opt/nginx/bin/nginx
```
### 1.3 设置开机自启动
```
mkdir -p ~/Library/LaunchAgents
cp /usr/local/opt/nginx/homebrew.mxcl.nginx.plist ~/Library/LaunchAgents/
# 设置开机启动
launchctl load -w ~/Library/LaunchAgents/homebrew.mxcl.nginx.plist
# 取消开机启动
launchctl unload ~/Library/LaunchAgents/homebrew.mxcl.nginx.plist
```
### 1.4 Nginx常用命令
```
sudo nginx #打开nginx
nginx -s reload | reopen | stop | quit #重新加载配置|重启|停止|退出
nginx -t #测试配置是否有语法错误
#如果提示pid丢失的话，就用这句话
nginx -c /usr/local/etc/nginx/nginx.conf
```
### 1.5 查看信息
点击http://localhost:8080 查看是否安装成功

## 二、安装PHP7.1

### 2.1 安装命令
```
brew install php71
```

### 2.2 设置全局变量
```
echo 'export PATH=/usr/local/bin:/usr/sbin:$PATH' >> ~/.bash_profile
source ~/.bash_profile
echo 'export PATH=/usr/local/Cellar/php@7.1/7.1.33/bin:$PATH' >> ~/.bashrc
source ~/.bashrc
```

### 2.3 设置开机自启动
```
mkdir -p ~/Library/LaunchAgents
cp /usr/local/opt/php@7.1/homebrew.mxcl.php@7.1.plist ~/Library/LaunchAgents/
# 设置开机启动
launchctl load -w ~/Library/LaunchAgents/homebrew.mxcl.php@7.1.plist
# 取消开机启动
launchctl unload ~/Library/LaunchAgents/homebrew.mxcl.php@7.1.plist
```
## 三、安装MySql

### 3.1 安装命令
```
brew install mysql
```

### 3.2 设置开机自启动
```
mkdir -p ~/Library/LaunchAgents
cp /usr/local/opt/php@7.1/homebrew.mxcl.mysql.plist ~/Library/LaunchAgents/
# 设置开机启动
launchctl load -w ~/Library/LaunchAgents/homebrew.mxcl.mysql.plist
# 取消开机启动
launchctl unload ~/Library/LaunchAgents/homebrew.mxcl.mysql.plist
```

### 3.3 设置root账户和密码
```
 #一直跟着提示走就行。
/usr/local/Cellar/mysql/8.0.18/bin/mysql_secure_installation
```
