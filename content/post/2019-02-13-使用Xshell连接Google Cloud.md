---
title: "使用Xshell连接Google Cloud"
date: "2019-02-13"
categories: 
  - "工具-效率"
tags: 
  - "工具-效率"
url: "/archives/497"
---

## 使用Xshell连接Google Cloud

标签（空格分隔）： 工具

* * *

\[toc\]

**前提：** 1. 科学上网 2. ssh工具，如Xshell，putty等. 3. Google Cloud服务器

本文以Xshell为例

### 生成密钥

1. 打开Xshell->工具->新建用户密钥生成向导。(密钥类型，长度默认即可)
2. 下一步->下一步。
3. 密钥名称(自己随便写，英文的，记住，最后一步要用到)
4. 输入密码->下一步。

### 在google cloud中注册公钥

1. 接上一个过程，复制生成的公钥；
2. 打开Google Cloud Platform；
3. Compute Engine -> 元数据 -> SSH密钥-> 修改；
4. 添加一项；
5. 将刚刚复制的公钥填进去，加一个空格然后输入密钥名称(Xshell生成密钥的时候自己填写的)。 如图所示： ![mark](https://image.i-ll.cc/blog/20190213/6nKL4iNhT9tj.png)
6. 保存

### 使用Xshell连接服务器

1. 填写基本服务器基本信息。
2. 如图，填写用户身份验证部分： ![mark](https://image.i-ll.cc/blog/20190213/eSanox2w3oKi.png)
3. 连接即可。

### 以root用户登入

ps:现在是2019年2月13日，经过以上操作后，是可以在xshell里面直接切换到root用户的。在Xshell里执行下面的命令。

> sudo -i #如果这条命令报错则需要进行后续步骤

1. 在Google Cloud Platform中选择对应的服务器，选择从浏览器窗口中打开；
2. 连接成功之后输入以下命令； >sudo -i #切换到root passwd #修改密码
3. 接着修改SSH配置文件/etc/ssh/sshd\_config；
    
    > vi /etc/ssh/sshd\_config #编辑文件 i #进入编辑模式
    
4. 找到以下内容并修改；
    
    > PermitRootLogin yes //默认为no，需要开启root用户访问改为yes PasswordAuthentication yes //默认为no，改为yes开启密码登陆
    
5. 修改完成后，再下按 esc 键，然后再输入
    
    > :wq #保存并退出
