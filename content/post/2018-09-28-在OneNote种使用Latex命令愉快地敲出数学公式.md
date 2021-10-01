---
title: "在OneNote种使用Latex命令愉快地敲出数学公式"
date: "2018-09-28"
categories: 
  - "工具-效率"
  - "考研之路"
url: "/archives/472"
---

### 在OneNote种使用Latex命令愉快地敲出数学公式

[office中所有支持键盘输入的公式](https://support.office.com/en-us/article/linear-format-equations-using-unicodemath-and-latex-in-word-2e00618d-b1fd-49d8-8cb4-8d17f25754f8?CorrelationId=44b66604-a275-4418-a724-93b48fecd6c1&ui=en-US&rs=en-US&ad=US)

office中默认是用的Unicodemath，相关的语法上个链接里面就有，office提供了Unicodemath与latex互转的方法。相关链接如下：[LaTeX Math in Office](https://blogs.msdn.microsoft.com/murrays/2017/07/30/latex-math-in-office/)

#### Unicodemath Latex互转步骤如下

默认是Unicodemath，此时部分Latex命令不管用。 ![](https://image.i-ll.cc/18-9-28/86184700.jpg)

1. 首先alt+=进入公式编辑状态；
2. 设计->左上角->工具->右下角->数学符号自动更正；
3. 按照下图输入(Unicodemath 转 Latex按照下图就行，反之改\\TEX 为 \\LF,改24C9为24C1即可) ![](https://image.i-ll.cc/18-9-28/12172957.jpg)
4. 然后alt+x,添加确定就ok。 alt+=进入数学公式编辑状态输入\\Tex就可以正常使用了，如需恢复默认，则只需要将\\Tex改成\\LF就可以了。

现在转成Latex之后\\frac就可以用了。 ![](https://image.i-ll.cc/18-9-28/35642871.jpg)
