---
title: "提取圣才电子书并转成PDF,epub,mobi,word等格式"
date: "2018-09-23"
categories: 
  - "工具-效率"
  - "考研之路"
url: "/archives/468"
---

\[toc\]

### Start

大四考研狗一名，本科计算机科学与技术，前面几个月一直准备继续读本专业，由于各种原因最终决定跨考管理科学与工程。学校指定教材是《管理学》罗宾斯，我买的第13版，由于是跨考，所以就想着找已经考上的学姐学长买一份笔记。。。奈何管科群太少。。。计科软件两个群加起来有2000+(算重复)，管科就没找到群，所以想到万能的淘宝，看到圣才教育有实体的笔记还送电子版，我只想要电子版。就下了APP，从淘宝评论中找了一个老哥的封面扫码领了电子版的书，233333。

#### 准备工作

**工具：** 电脑一台 夜神模拟器 calibre VScode编辑器\[推荐\] (或者notepad++等可以使用正则表达式的编辑器) fnr软件(后面给出了下载地址) **注意：推荐大家根据2019.02.22更新，简单方法去除乱码，这样的话无需下载VScode**

#### 操作开始

1. 如上所说，需要哪本资料，就得找到那本资料的封面二维码，扫码用自己手机号注册领取。
2. 电脑下载夜神模拟器，安装圣才电子书APP。
3. 登陆并在礼包中找到电子书 ![1](https://image.i-ll.cc/18-9-23/32959219.jpg)
4. 打开夜神模拟器，文件管理器，搜索shengcai，进入read目录。 ![2](https://image.i-ll.cc/18-9-23/98611882.jpg)
5. 纯数字的目录就是我们要找的电子书目录。 ![3](https://image.i-ll.cc/18-9-23/28888200.jpg)
6. 选中这两个目录，按照这个链接里面的操作，[复制文件到和电脑的共享目录中](https://www.yeshen.com/faqs/rJM_efyxZ "复制文件到和电脑的共享目录中")
7. 选中epub文件夹，参考下一部分2019.02.22更新的内容，然后打包成zip或者rar文件就可以了，别的文件不用管。 ![4](https://image.i-ll.cc/18-9-23/82766790.jpg)
8. 打开Calibre，添加书籍，从单个目录添加书籍，选择刚刚打包好的压缩包即可。
9. 最后选中书籍，右键转换，就可以转换成你想要的任何格式了。

#### 2019.02.22更新，解决乱码问题

解压出来之后，大家可以看到直接打开epub文件夹下面的html文件之后显示的是乱码！ [![乱码](https://image.i-ll.cc/blog/20190222/7LyMhcygfXUi.png "乱码")](https://image.i-ll.cc/blog/20190222/7LyMhcygfXUi.png "乱码")

我们使用VScode打开epub文件夹，可以看到有很多html文件，我们只需要改动html文件的内容就可以，随便打开一个html文件，可以看到新版圣才APP在html源文件中添加了以下代码，导致我们直接打开看到的内容是乱码。 [![乱码2](https://image.i-ll.cc/blog/20190222/Cj3W21PTNsbT.png "乱码")](https://image.i-ll.cc/blog/20190222/Cj3W21PTNsbT.png "乱码")

其实解决方法很简单，只需要把这些东西在源码中一个一个删掉即可。

但是问题来了！ 如何批量删除？

我们可以利用正则表达式来匹配。

匹配两个字符串匹配字符串中间的内容语法如下： 1. 匹配两个字符串A与B中间的字符串包含A与B： 表达式: A._?B 示例: Abaidu.comB 结果: Awww.apizl.comB 2. 匹配两个字符串A与B中间的字符串包含A但是不包含B： 表达式: A._?(?=B) 示例: Awww.apizl.comB 结果: Awww.apizl.com 3. 匹配两个字符串A与B中间的字符串且不包含A与B： 表达式: (?<=A).\*?(?=B) 示例: Awww.baidu.comB 结果: www.baidu.com

在VScode里面按快捷键ctrl+H，然后点击下图这个按钮使用正则表达式按照以下步骤操作即可。 ![mark](https://image.i-ll.cc/blog/20190222/iFXBPfrBrQ1d.png)

1. 首先去掉标签blurp中的内容，包括它本身。输入以下代码

```re
\s*<blurp>\n.*?\s*</blurp>
```

大家可以看到标签包括它本身已经被选中了。 ![mark](https://image.i-ll.cc/blog/20190222/9jUNPlehNAfJ.png) 点击Replace of all即可完成替换。

2. 去掉&lt;blurp&gt;与&lt;/blurp&gt;之间的乱码，包括它们本身。输入以下代码。

```re
<blurp>.*?</blurp>
```

如图所示： ![mark](https://image.i-ll.cc/blog/20190222/unVJYU07obUT.png) 全部替换。

3. 删掉style="display: none;"这个就很简单了，直接替换就行。

```re
style="display: none;"
```

这样我们一个页面就改好了。其他页面就重复这样修改就行了。 ![mark](https://image.i-ll.cc/blog/20190222/lW4sC7fwmi7J.png)

#### 2019.02.22更新，简单办法去除乱码

本想自己写一个批量处理的脚本，结果发现已经有了类似的软件。下面我直接给出下载地址。[fnr下载地址](http://findandreplace.io/ "fnr下载地址")，随便解压到哪里都可以。

1. 打开fnr.exe;
2. 修改Dir为.epub/OEBPS结尾的路径，.指的是你要提取的电子书目录;比如 ![mark](https://image.i-ll.cc/blog/20190222/vEXIqEx1vsFR.png)
3. File Mask(需要处理的文件类型)中填写\*.html;
4. 其实这里填不填都不影响,Exclude Mask(不处理的文件类型)中填写
    
    > \*.xml, \*.ncx, \*.opf, \*.css, \*.ttf
    
5. Use regular expressions前面打勾;
    
6. 依次输入以下代码并替换(Replace)即可(共三条,一行一条)。

```re
\s*<blurp>\n.*?\s*</blurp>
<blurp>.*?</blurp>
style="display: none;"
```

#### 重要提示！！！

由于markdown编辑器的问题，需要用到的三行代码其实是以下这样的，可能有的同学显示的有问题导致出错。前两行代码按照下图自己手敲，最后一行代码肯定不会显示出错。**符号都为英文半角！！！** **符号都为英文半角！！！** **符号都为英文半角！！！** 重要的事情说三遍！

![mark](https://image.i-ll.cc/blog/20190223/1nDbPndiEO7w.png)

#### 更新

\---- 2018.12.12 ---- 有朋友反应电子书提取出来有乱码的情况，经过排查是APP版本问题。早期版本下载如下： 链接：https://pan.baidu.com/s/1d2nhgpm834AdKkkRw84cFg 提取码：9l8x

\---- 2018.12.24 ---- 有朋友用新版本的夜神模拟器+低版本的圣才电子书APP同样出现了乱码情况。我已将我使用的夜神模拟器一并上传到百度网盘中。 链接：https://pan.baidu.com/s/1d2nhgpm834AdKkkRw84cFg 提取码：9l8x

\---- 2019.02.22 ---- 更新一系列步骤，解决圣才电子书新版APP乱码问题。

若碰到其他问题，请及时向我反映。

**联系方式：**

企鹅：447600334 Email：dandanv5@hotmail.com
