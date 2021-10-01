---
title: "初识Git  如何使用Git将本地项目上传到Github"
date: "2017-10-29"
categories: 
  - "工具-效率"
  - "计协微信"
tags: 
  - "git"
url: "/archives/198"
---

# 什么是Git？

Git是一款免费、开源、世界上最先进的分布式版本控制系统，用于敏捷高效地处理任何或小或大的项目。

## 什么是版本控制系统？

![举个栗子](https://image.i-ll.cc//uPic/20200611/OFmNdy.png?imageMogr2/auto-orient/blur/1x0/quality/75|watermark/2/text/WmhhbyBDaGnigJhzIEJsb2c=/font/dGltZXMgbmV3IHJvbWFu/fontsize/240/fill/IzAwMDAwMA==/dissolve/75/gravity/SouthEast/dx/10/dy/10|imageslim)

上图实际上是一个文档的好几个不同的版本，当我们每次作出修改，却害怕自己修改的东西以后会用到，怎么办？只能创建多个文件用来记录，但是等到后面要用的时候在一个一个翻出来找就很麻烦了。

这时候就需要一个软件协助我们管理项目，恰好git就是这么一个软件，它还可以让其他伙伴协助我们编辑，它可以记录每次文件的改动，以及改动内容。举个栗子

![举个栗子](https://image.i-ll.cc//uPic/20200611/MsWymh.png?imageMogr2/auto-orient/blur/1x0/quality/75|watermark/2/text/WmhhbyBDaGnigJhzIEJsb2c=/font/dGltZXMgbmV3IHJvbWFu/fontsize/240/fill/IzAwMDAwMA==/dissolve/75/gravity/SouthEast/dx/10/dy/10|imageslim)

关于git的详细教程大家可以看看廖雪峰老师的[Git教程](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000)

大家应该也有过如下经历，经常要用不同的电脑工作，这时候文件就不得不放到U盘里面，每次办公结束还需要把U盘里面的文件更新一下。哪天一不小心忘记更新了，但是工作还得继续啊！怎么办？只能跑回电脑旁边重新插上U盘更新。

这时候我们就需要将我们本地的项目传到云端，需要使用的时候直接从云端拿回本地，修改完毕之后直接同步到云端。这样是不是很方便呢？像这样的托管平台有Github、国内有码云等。

以Github为例，做以下演示：

# 用git将本地项目上传到github

1. www.github.com 注册账号
    
2. 登录->新建仓库 如下图
    

![举个栗子](https://image.i-ll.cc//uPic/20200611/7l9U1B.png?imageMogr2/auto-orient/blur/1x0/quality/75|watermark/2/text/WmhhbyBDaGnigJhzIEJsb2c=/font/dGltZXMgbmV3IHJvbWFu/fontsize/240/fill/IzAwMDAwMA==/dissolve/75/gravity/SouthEast/dx/10/dy/10|imageslim)

![举个栗子](https://image.i-ll.cc//uPic/20200611/uTp4t5.png?imageMogr2/auto-orient/blur/1x0/quality/75|watermark/2/text/WmhhbyBDaGnigJhzIEJsb2c=/font/dGltZXMgbmV3IHJvbWFu/fontsize/240/fill/IzAwMDAwMA==/dissolve/75/gravity/SouthEast/dx/10/dy/10|imageslim) 3. github是一个托管平台，我们还需要安装git，下载地址：https://git-scm.com/downloads 安装过程看上面廖雪峰老师的教程

1. 安装好git之后，打开Git Bash ![举个栗子](https://image.i-ll.cc//uPic/20200611/VlIeMK.png?imageMogr2/auto-orient/blur/1x0/quality/75|watermark/2/text/WmhhbyBDaGnigJhzIEJsb2c=/font/dGltZXMgbmV3IHJvbWFu/fontsize/240/fill/IzAwMDAwMA==/dissolve/75/gravity/SouthEast/dx/10/dy/10|imageslim) ![举个栗子](https://image.i-ll.cc//uPic/20200611/Xbx9N4.png?imageMogr2/auto-orient/blur/1x0/quality/75|watermark/2/text/WmhhbyBDaGnigJhzIEJsb2c=/font/dGltZXMgbmV3IHJvbWFu/fontsize/240/fill/IzAwMDAwMA==/dissolve/75/gravity/SouthEast/dx/10/dy/10|imageslim)
2. 我的项目放在G:\\Numpy\_Learning

## 开始进入正题

1. 初始化本地仓库
    
    > git init
    
2. 在本地创建ssh\_key
    
    > ssh-keygen -t rsa -C "your\_email@youremail.com"
    
    your\_email@youremail.com为你注册github的邮箱，我的是dandanv5@hotmail.com，所以命令为:
    
    > ssh-keygen -t rsa -C "dandanv5@hotmail.com"
    
    不设密码，输入y，直接回车出现以下界面就说明生成成功。
    
    ![举个栗子](https://image.i-ll.cc//uPic/20200611/5ZINwu.png?imageMogr2/auto-orient/blur/1x0/quality/75|watermark/2/text/WmhhbyBDaGnigJhzIEJsb2c=/font/dGltZXMgbmV3IHJvbWFu/fontsize/240/fill/IzAwMDAwMA==/dissolve/75/gravity/SouthEast/dx/10/dy/10|imageslim)
    
    进入图中提示的地址，用记事本打开id\_rsa.pub，全部复制。
    
    ![举个栗子](https://image.i-ll.cc//uPic/20200611/9AnEqM.png?imageMogr2/auto-orient/blur/1x0/quality/75|watermark/2/text/WmhhbyBDaGnigJhzIEJsb2c=/font/dGltZXMgbmV3IHJvbWFu/fontsize/240/fill/IzAwMDAwMA==/dissolve/75/gravity/SouthEast/dx/10/dy/10|imageslim) New SSH Key
    
    ![举个栗子](https://image.i-ll.cc//uPic/20200611/Htgjrg.png?imageMogr2/auto-orient/blur/1x0/quality/75|watermark/2/text/WmhhbyBDaGnigJhzIEJsb2c=/font/dGltZXMgbmV3IHJvbWFu/fontsize/240/fill/IzAwMDAwMA==/dissolve/75/gravity/SouthEast/dx/10/dy/10|imageslim) Add SSH Key
    
    这样SSH Key就添加进去了
    
3. 输入`ssh -T git@github.com`看看是否添加成功
    
    ![举个栗子](https://image.i-ll.cc//uPic/20200611/0Ui5Lb.png?imageMogr2/auto-orient/blur/1x0/quality/75|watermark/2/text/WmhhbyBDaGnigJhzIEJsb2c=/font/dGltZXMgbmV3IHJvbWFu/fontsize/240/fill/IzAwMDAwMA==/dissolve/75/gravity/SouthEast/dx/10/dy/10|imageslim)
    
4. 现在我们就可以把自己本地的项目传到github了， 先配置username和Email
    
    ```null
    git config --global user.name "mlzc"
    git config --global user.email "dandanv5@hotmail.com"
    ```
    
5. 进入要上传的远程仓库，添加远程地址
    
    > git remote add origin https://github.com/MLZC/Numpy\_Learning.git
    
6. 创建一个文件 README.md，并写入# Numpy\_Learning
    
    > echo "# Numpy\_Learning" >> README.md
    
    这时候目录下会多一个文件 README.md，里面的内容是# Numpy\_Learning
    
7. 在本地仓库添加文件
    
    ```null
    git add README.md
    git commit -m "first commit"
    ```
    
    添加本地仓库下的所有文件
    
    > git add .
    
8. 提交上传
    
    > git push -u origin master
    
9. 提交成功
    
    ![举个栗子](https://image.i-ll.cc//uPic/20200611/YBEfPX.png?imageMogr2/auto-orient/blur/1x0/quality/75|watermark/2/text/WmhhbyBDaGnigJhzIEJsb2c=/font/dGltZXMgbmV3IHJvbWFu/fontsize/240/fill/IzAwMDAwMA==/dissolve/75/gravity/SouthEast/dx/10/dy/10|imageslim) 这样就成功的将本地的项目推送到云端了。
    

注：

- git push 将本地仓库推送到远程仓库
- git pull 将远程仓库里面的文件取回到本地
- 修改完代码后可以用 git status 查看文件的差别

当然不想使用命令的话也可以直接使用github客户端，客户端使用很简单，这里就不详细介绍了。

常用 Git 命令清单:[查看阮一峰老师的日志](http://www.ruanyifeng.com/blog/2015/12/git-cheat-sheet.html)
