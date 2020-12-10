---
title: Mysql修改root密码的4种方法
date: 2020-12-10 12:28:46
tags: -Mysql
categories: [数据库]
thumbnail: https://d1.awsstatic.com/asset-repository/products/amazon-rds/1024px-MySQL.ff87215b43fd7292af172e2a5d9b844217262571.png
---

### 1： 用SET PASSWORD命令
首先登录MySQL。
```
-- 格式：mysql>
set password for 用户名@localhost = password(‘新密码’);
-- 例子：mysql>
set password for root@localhost = password(‘123’);
```
### 2：用mysqladmin
```
-- 格式：
mysqladmin -u用户名 -p旧密码 password 新密码
-- 例子：
mysqladmin -uroot -p123456 password 123
```
### 3：用UPDATE直接编辑user表
首先登录MySQL。
```
use mysql;
update user set password=password(‘123’) where user=’root’ and host=’localhost’;
flush privileges;
```
### 4：在忘记root密码的时候，可以这样
以windows为例：

关闭正在运行的MySQL服务。
打开DOS窗口，转到mysql\bin目录。
输入mysqld –skip-grant-tables 回车。–skip-grant-tables 的意思是启动MySQL服务的时候跳过权限表认证。
再开一个DOS窗口（因为刚才那个DOS窗口已经不能动了），转到mysql\bin目录。
输入mysql回车，如果成功，将出现MySQL提示符 >。
连接权限数据库： use mysql; 。
改密码：update user set password=password(“123”) where user=”root”;（别忘了最后加分号） 。
刷新权限（必须步骤）：flush privileges;　。
退出 quit。
注销系统，再进入，使用用户名root和刚才设置的新密码123登录。
