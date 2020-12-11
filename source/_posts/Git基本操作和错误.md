---
title: Git基本操作和错误
date: 2020-12-11 12:08:32
tags: -Git
categories: [Git]
name: XiaoGang
---

## Git基本操作和错误
### 本地创建仓库操作
```bash
# 创建本地仓库
git init

#将文件添加进Git
git add 文件名  
git add . #将所有的文件全部添加到Git

#提交
git commit -m "描述信息"

#删除文件或文件夹
git rm -r --cached target              # 删除target文件夹
git commit -m '删除了target'        # 提交,添加操作说明
```
### Git远程仓库操作
```bash
# 创建SSH Key
ssh-keygen -t rsa -C "youremail@example.com"

#查看远程仓库
git remote -v

#添加远程仓库
#git remote add 名称 远程仓库地址
git remote add origin git@git.coding.net:pgw1314/shells.git

推送的远程仓库
#git push 仓库名  分支
git push origin master

更新远程仓库
#git pull 仓库名 分支
git pull origin master

删除远程仓库
git remote remove 仓库名称
```
