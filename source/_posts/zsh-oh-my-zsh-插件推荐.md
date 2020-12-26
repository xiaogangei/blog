---
title: zsh oh-my-zsh 插件推荐
name: XiaoGang
date: 2020-12-26 01:53:17
tags:
	- 插件
categories: [Mac]
headimg: https://s3.ax1x.com/2020/12/26/rhxqO0.jpg
---
在这里整理了一些Mac上ZSH中的常用的插件，使用这些插件可大大提升我们的工作效率。
<!--more-->
原文链接：[https://hufangyun.com/2017/zsh-plugin/](https://hufangyun.com/2017/zsh-plugin/)
### Git
{% note 默认已开启 %}

#### 作用

可以使用各种 git 命令缩写。😋

比如
```
git add --all ===> gaa

git commit -m ===> gcmsg
```

![rfdWwR.png](https://s3.ax1x.com/2020/12/26/rfdWwR.png)

查看所有 git 命令缩写
```
cat ~/.oh-my-zsh/plugins/git/git.plugin.zsh
```
或者筛选对应的命令

如和 config 有关的命令
```
alias | grep config
```
### autojump
[autojump 官网](https://github.com/wting/autojump)

#### 作用
{% note  目录间快速跳转,不用再一直 cd 了 😁 %}

#### 使用

使用 autojump 的缩写 j

cd 命令进入 ~/user/github/Youthink 文件夹，下一次再想进入 Yourhink 文件夹的时候,直接 j youthink 即可
或者只输入 youthink 的一部分 youth 都行
删除无效路径
```
j --purge 无效路径
```
打开 muisc 文件夹
```
jo music
```
多个参数一起使用 打开 /home/user/work/inbox
```
j w in
```
和 Z 不同 autojump 不是 zsh 内置的插件，需要额外安装。
首先安装 autojump，如果你用 Mac，可以使用 brew 安装：
```
brew install autojump
```
如果是 Linux，可以使用 git 安装，比如：
```
git clone git://github.com/joelthelion/autojump.git
```
进入目录，执行
```
./install.py
```
最后把以下代码加入 .zshrc：
```
[[ -s ~/.autojump/etc/profile.d/autojump.sh ]] && . ~/.autojump/etc/profile.d/autojump.sh

```
### Z
如果你不想额外安装 autojump
可以使用 oh-my-zsh 内置的类似组件 Z
和 autojump 除了名字不一样，基本雷同。
```
z -x 无效路径
```
效果图
![rfdfT1.jpg](https://s3.ax1x.com/2020/12/26/rfdfT1.jpg)

### zsh-syntax-highlighting
[官网](https://github.com/zsh-users/zsh-syntax-highlighting)

作用 平常用的ls、cd 等命令输入正确会绿色高亮显示，输入错误会显示其他的颜色。

<img src="https://s3.ax1x.com/2020/12/26/rfwk0s.jpg" alt="rfwk0s.jpg" border="0">

#### 安装

克隆项目
```
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
```
#### 在 ~/.zshrc 中配置

```
plugins=(其他的插件 zsh-syntax-highlighting)
```
使配置生效
```
source ~/.zshrc
```
### zsh-autosuggestions
[官网](https://github.com/zsh-users/zsh-autosuggestions)

#### 作用

效率神器 👍

如图输入命令时，会给出建议的命令（灰色部分）按键盘 → 补全

<img src="https://s3.ax1x.com/2020/12/26/rfwFmj.png" alt="rfwFmj.png" border="0">

安装

克隆项目
```
git clone git://github.com/zsh-users/zsh-autosuggestions $ZSH_CUSTOM/plugins/zsh-autosuggestions
```
在 ~/.zshrc 中配置
```
plugins=(其他的插件 zsh-autosuggestions)
```
使配置生效
```
source ~/.zshrc
```

如果感觉 → 补全不方便，还可以自定义补全的快捷键，比如我设置的逗号补全
```
bindkey ',' autosuggest-accept
```
在 .zshrc 文件添加这句话即可。

### sublime
[官网](https://github.com/robbyrussell/oh-my-zsh/tree/master/plugins/sublime)

已经内置直接启用即可

#### 作用

在命令行使用 Sublime Text 打开文件、项目

|命令|	作用|
| ---- | ---- |
|st	|打开 sublime|
|st + 文件夹	|打开该文件夹|
|st + 文件	|打开该文件|
|stt	|打开当前的文件夹，相当于 st .|
|sst	|管理员权限 相当于 sudo st|

### git-open
[官网](https://github.com/paulirish/git-open)

在终端里打开当前项目的远程仓库地址

不要小看这个插件欧，每次改完本地代码，当你想用浏览器访问远程仓库的时候，就知道这个插件多方便了 😘

支持打开的远程仓库

- github.com
- gist.github.com
- gitlab.com
- 自定义域名的 GitLab
- bitbucket.org
- Atlassian Bitbucket Server (formerly Atlassian Stash)
- Visual Studio Team Services
- Team Foundation Server (on-premises)
#### 安装

克隆项目
```
git clone https://github.com/paulirish/git-open.git $ZSH_CUSTOM/plugins/git-open
```
在 ~/.zshrc 中配置
```
plugins=(其他的插件 git-open)
```
使配置生效
```
source ~/.zshrc
```
### 其他
我在 .zshrc 中的其他配置

history 命令时间格式
history 命令查看历史输入命令的时间展示格式
```
HIST_STAMPS="yyyy-mm-dd"
```

时间会按照指定的格式展示，方便搜索查看

#### 主题
在 ~/.zshrc 文件中设置主题为 random 即可开启随机主题
```
ZSH_THEME="random"
```
每次打开新的终端的时候，zsh 都会随机使用一个主题

别名
```
alias go="git-open"
alias rm="trash"
```
安装了一个 trash 命令，替代 rm 命令，被删除的文件会放到垃圾桶

[trash 官网](https://github.com/sindresorhus/trash)

安装方式
```
npm install --global trash-cli
```
```
alias cp="cp -i"
```
防止 copy 的时候覆盖已存在的文件, 带上 i 选项，文件已存在的时候，会提示，需要确认才能 copy

### Bat
#### 作用
{% note
bat 代替 cat
cat 某个文件，可以在终端直接输出文件内容，bat 相比 cat 增加了行号和颜色高亮 👍
 %}
直接上个效果
![rfw1B9.jpg](https://s3.ax1x.com/2020/12/26/rfw1B9.jpg)

[官网](https://github.com/sharkdp/bat)

安装方式

macOS 上
```
brew install bat
```
