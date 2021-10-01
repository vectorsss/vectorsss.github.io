---
title: "MacOS Catalina 10.15.4 alias添加自定义命令"
date: "2020-04-14"
categories: 
  - "工具-效率"
tags: 
  - "macos"
url: "/archives/551"
---

例如:简化命令'clear'为'c'  
在之前的版本中,bash\_profile和bashrc

首先打开终端:

> vim ~/.bash\_profile

然后添加如下代码.

```{shell}
alias c = 'clear'
```

完了之后在终端执行

> source ~/.bash\_profile

但是这么操作的话,这个简化命令仅在当前终端有效.

实际上相当于在终端直接定义命令的别名:

> alias c = 'clear'

~/.bashrc 启动终端的时候会自动执行该文件里面的命令. 所以需要在文件~/.bashrc中添加一行.

> source ~/.bash\_profile

macOS Catalina 10.15.4 中没有~/.bashrc文件,取而代之的是~/.zshrc. 所以以上对~/.bashrc文件的操作改为对~/.zshrc即可.

```{shell}
vim ~/.bash_profile
# 添加自定义命令
alias c = 'clear'
```

```{shell}
vim ~/.zshrc
# 添加命令
source ~/.bash_profile
```

这样就可以了.
