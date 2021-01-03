---
title: Mac中常用的一些代码
name: XiaoGang
date: 2021-01-04 05:55:51
tags:
- 代码
categories: [Mac]
---
Mac中经常用到的一些代码做了一些整理，方便以后使用
<!--more -->

## 软件安装
### Homebrew 安装

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```
### Oh-my-zsh安装

```bash
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

### Oh-my-zsh插件安装
#### autojump安装

```bash
# homebrew安装
brew install autojump
# git安装
git clone git://github.com/joelthelion/autojump.git
# 进入目录执行
./install.py
```
安装完成后将下面代码添加到'~/.zshrc'文件中

```bash
[[ -s ~/.autojump/etc/profile.d/autojump.sh ]] && . ~/.autojump/etc/profile.d/autojump.sh

```


#### zsh-syntax-highlighting安装
安装
```bash
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting

```
在`~/.zshrc`文件中配置

```bash

plugins=(其他的插件 zsh-syntax-highlighting)

```
使配置生效

```bash
source ~/.zshrc
```

#### zsh-autosuggestions安装


```bash
git clone git://github.com/zsh-users/zsh-autosuggestions $ZSH_CUSTOM/plugins/zsh-autosuggestions

```
在`~/.zshrc`文件中配置

```bash
plugins=(其他的插件 zsh-autosuggestions)
```
使配置生效

```bash
source ~/.zshrc
```
如果感觉 → 补全不方便，还可以自定义补全的快捷键，比如我设置的逗号补全
在` .zshrc` 文件添加这句话即可。
```bash
bindkey ',' autosuggest-accept

```
### ADB安装
安装
```bash
brew install -cask android-platform-tools
```
查看链接的设备
```bash
adb devices
```
## 网络设置
###  Mac终端设置代理访问
#### 临时设置
```bash
export http_proxy=http://proxyAddress:port
```
#### 永久设置

把代理服务器地址写入 shell 配置文件 .bashrc 或者 .zshrc 直接在 .bashrc 或者 .zshrc 添加下面内容
```bash
export http_proxy="http://localhost:port"
export https_proxy="http://localhost:port"

```
#### 可切换设置

把以下的文本放置到 .bashrc 或者 .zshrc 中, 可以在使用的时候执行 proxy, 不使用的时候执行 unproxy
```bash
alias proxy='export all_proxy=socks5://127.0.0.1:1086'
alias unproxy='unset all_proxy'

```

### Mac终端查看公网IP
在`~/.zshrc`中添加下面代码
```bash
alias cip='curl icanhazip.com'
```
备用
```bash
curl icanhazip.com
curl ifconfig.me
curl curlmyip.com
curl ip.appspot.com
curl ipinfo.io/ip
curl ipecho.net/plain
curl www.trackip.net/i
```

## 磁盘操作
### Mac分区挂载

##### 查看硬盘分区列表

```bash
diskutil list
```
##### 挂载分区

```bash
# 格式 sudo diskutil mount 识别码
sudo diskutil mount disk1s1
```
