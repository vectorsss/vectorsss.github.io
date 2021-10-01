---
title: "Visual Studio Code & LaTeX Workshop 优雅地编写Latex文档 , 完美支持中文"
date: "2017-11-03"
categories: 
  - "工具-效率"
tags: 
  - "latex"
url: "/archives/214"
---

LATEX 是基于 Tex 的排版系统，多用于排版高质量的科技类和数学类文档。

# Tex Live

TexLive是tex的集合环境，包含了pdfletex，xeletex等编译器。 下载地址: http://ctan.mirrors.hoobly.com/systems/texlive/Images/texlive2017-20170524.iso 安装过程: https://zhuanlan.zhihu.com/p/19779481?columnSlug=LaTeX

# Visual Studio Code

[Visual Studio Code](https://code.visualstudio.com/),一款强大的跨平台编辑器。

# Latex Workshop

[Latex Wordshop](https://marketplace.visualstudio.com/items?itemName=James-Yu.latex-workshop) 是 Visual Studio Code 下的一个扩展，可编译、反定向、有代码提示。

安装好Tex Live 和 vscode 之后，直接在扩展里面搜索Latex Workshop并安装。

Latex Workshop默认是用pdflatex编译的，我们将他改成Xelatex后即可完美支持中文。

修改方法如下：

> ctrl+,

搜索latex-workshop.latex.toolchain->右键 Replace in Setting->修改为如下代码

```json
    "latex-workshop.latex.toolchain": [
        {
            "command": "xelatex",
            "args": [
                "-synctex=1",
                "-interaction=nonstopmode",
                "-file-line-error",
                "%DOC%"
            ]
        }, {
            "command": "bibtex",
            "args": [
                "%DOCFILE%"
            ]
        }, {
            "command": "xelatex",
            "args": [
                "-synctex=1",
                "-interaction=nonstopmode",
                "-file-line-error",
                "%DOC%"
            ]
        }, {
            "command": "xelatex",
            "args": [
                "-synctex=1",
                "-interaction=nonstopmode",
                "-file-line-error",
                "%DOC%"
            ]
        }
    ]
```

这样就配置结束了，ctrl+alt+b编译，ctrl+alt+t查看。
