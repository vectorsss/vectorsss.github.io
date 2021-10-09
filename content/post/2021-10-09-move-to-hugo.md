---
title: "完美迁移博客从wordpress到hugo"
subtitle:    ""
description: "完美迁移博客从wordpress到hugo，包括xml解析、图床的完美迁移以及保持文章原始链接不变。"
date: 2021-10-09T13:00:04+03:00
lastmod: 2021-10-09T13:00:04+03:00
tags: ["hugo", "工具-效率"]
categories: ["工具-效率"]
author: "Chi Zhao(Vector)"
keywords: ["wordpress", "hugo"]
slug: "2021-10-09-move-to-hugo"
draft: false
hiddenFromHomePage: false
hideHeaderAndFooter: false
---


## 前言

博客一直在阿里云学生机上托管，使用wordpress。自从上了研究生之后博客也就一直荒废了。服务器9月底到期，本想着继续续费一下学生机就不需要再折腾一遍了。但是由于已经不在国内读书了，没法进行学生认证。只好将博客迁移到**hugo**。迁移到**Hugo**而不是**Hexo**的原因主要是因为**hugo**对**Rmarkdown**的支持更好。
<!--more-->

## 网站情况简介

开始介绍迁移过程之前，我先简单说一下我网站的基本情况供大家参考。如果大家网站情况和我一样，那完全可以采用跟我相同的迁移方案。

笔者从16年开始写博客，很早之前在简书上随便写一写，然后迁移到了csdn。后来由于在第三方网站上写作不自由，所以就自建博客了。在简书和csdn写作期间，都是用的**平台自己的图床**，直到自建博客开始才开始使用七牛云的OSS服务，每月免费10G但是仅限http流量，2020年我才将图床也全部升级为https调用。

图床迁移实际上并不是一件容易的事情，因为目前所有的迁移工具都是只能**识别markdown语法**的图片链接而不是**html标签**里面的链接。这就导致我们必须将Wordpress中的所有文章全部转成**markdown语法**。

最后一个问题就是保证文章的链接迁移前后没有变化，这样就可以保证拥有旧链接的人们可以正常访问。

综上，我们需要解决三个问题：

1. 解析Wordpress备份的"XML"为拥有markdown语法的".md"文件；
2. 图床迁移；
3. 固定链接。

## 方案对比

当然，我们可以直接选择官网给出的方案[Migrate to Hugo](https://gohugo.io/tools/migrations/)。对于wordpress，主要有以下几种。
![wordpress migrate to hugo](https://image.i-ll.cc//uPic/20211009/Drxefh.png?imageMogr2/auto-orient/blur/1x0/quality/75|watermark/2/text/WmhhbyBDaGnigJhzIEJsb2c=/font/dGltZXMgbmV3IHJvbWFu/fontsize/240/fill/IzAwMDAwMA==/dissolve/75/gravity/SouthEast/dx/10/dy/10|imageslim)
这几种方案我都尝试过，各有优势却都不完美。以下是详细说明

1. [wordpress-to-hugo-exporter](https://github.com/SchumacherFM/wordpress-to-hugo-exporter)： 可以导出，且文件名称就是带有日期和中文的标题名称。但是不是原生markdown格式。而是如下图所示的结构。不满足需求1，2，所以**排除**。

    ![content inside markdown](https://image.i-ll.cc//uPic/20211010/InznCv.png?imageMogr2/auto-orient/blur/1x0/quality/75|watermark/2/text/WmhhbyBDaGnigJhzIEJsb2c=/font/dGltZXMgbmV3IHJvbWFu/fontsize/240/fill/IzAwMDAwMA==/dissolve/75/gravity/SouthEast/dx/10/dy/10|imageslim)

2. [exitwp-for-hugo](https://github.com/wooni005/exitwp-for-hugo): 原始仓库是用python2.x写的，但是有人完善了python3.x的版本。这个程序可以将Wordpress的xml文件转成markdown语法的md文件，但是文件名太乱。（因为标题中包含了中文，所以这个程序会自动将中文转成unicode编码然后用它作为文件名储存在电脑中）

    ![file name structure - exitwp-for-hugo](https://image.i-ll.cc//uPic/20211010/x3GmFS.png?imageMogr2/auto-orient/blur/1x0/quality/75|watermark/2/text/WmhhbyBDaGnigJhzIEJsb2c=/font/dGltZXMgbmV3IHJvbWFu/fontsize/240/fill/IzAwMDAwMA==/dissolve/75/gravity/SouthEast/dx/10/dy/10|imageslim)

3. [blog2md](https://github.com/palaniraja/blog2md): 与[exitwp-for-hugo](https://github.com/wooni005/exitwp-for-hugo)类似，文件名太乱且不包含日期。

    ![file name structure - blog2md](https://image.i-ll.cc//uPic/20211010/8JNn1t.png?imageMogr2/auto-orient/blur/1x0/quality/75|watermark/2/text/WmhhbyBDaGnigJhzIEJsb2c=/font/dGltZXMgbmV3IHJvbWFu/fontsize/240/fill/IzAwMDAwMA==/dissolve/75/gravity/SouthEast/dx/10/dy/10|imageslim)

4. [wordhugopress](https://github.com/nantipov/wordhugopress): java写的程序，对于新手不太友好，但是也可以基于Wordpress博客中的文章生成markdown语法的md文件。需要配置数据库用户名和密码，而且最后生成的目录结构很乱。

    ![output structure - wordhugopress](https://image.i-ll.cc//uPic/20211010/By0AxI.png?imageMogr2/auto-orient/blur/1x0/quality/75|watermark/2/text/WmhhbyBDaGnigJhzIEJsb2c=/font/dGltZXMgbmV3IHJvbWFu/fontsize/240/fill/IzAwMDAwMA==/dissolve/75/gravity/SouthEast/dx/10/dy/10|imageslim)

然后突然发现一个仓库[wordpress-export-to-markdow_L版](https://github.com/AvantaR/wordpress-export-to-markdown)，这个只需要自己在电脑上安装node.js环境，然后就可以直接运行了。它可以解决除**固定链接**以外的所有问题，是一个近乎完美的方案。基于L版，[AvantaR](https://github.com/AvantaR)，在markdown的yaml头文件中添加了**slug**参数，详细实现见该仓库[wordpress-export-to-markdow_A版](https://github.com/AvantaR/wordpress-export-to-markdown)。

实际上**slug**和**url**还是有区别的。以下面这个yaml头和网站[https://blog.i-ll.cc](https://blog.i-ll.cc)为例：

```yaml
title: "Drcom下如何优雅地使用路由器上网"
date: "2016-12-23"
categories: 
  - "other"
tags: 
  - "路由器"
url: "/archives/108"
```

上面的配置文件中使用了**url**，所以该文章最后的链接是[https://blog.i-ll.cc/archives/108/](https://blog.i-ll.cc/archives/108/)。如果将**url**改为**slug**，如下所示。

```yaml
title: "Drcom下如何优雅地使用路由器上网"
date: "2016-12-23"
categories: 
  - "other"
tags: 
  - "路由器"
slug: "/archives/108"
```

那么该文章最后的链接是[https://blog.i-ll.cc/post/archives/108/](https://blog.i-ll.cc/post/archives/108/)。

两者的区别就是**slug**指的是文章的缩写名，在最后生成的文章链接中，会在前面加上文章所在的目录名（根域名+目录名+slug参数对应的值）（上面的例子中，目录名是post），而**url**后面的参数就是直接添加到根域名下的参数。因为我网站的固定连接下没有post路径，所以我在L版的基础上进行了修改得到了M版[wordpress-export-to-markdown_M](https://github.com/MLZC/wordpress-export-to-markdown)以达到我自己的需求。

## 最终方案使用说明

### 转换Wordpress xml以及保持文章链接不变

使用方法就是直接clone该仓库，然后将Wordpress的xml文件放到该程序的根目录下并改名为*export.xml*, 然后执行下面的命令。因为我修改了一些默认参数，所以可以设置`--wizard=false`， 当然，如果你们像自己更改默认值，可以去掉`--wizard=false`。

```shell
npm install && node index.js --wizard=false
```

### 图床迁移

这部分实际上没有什么好说的，主要使用这两个软件，都是图形化界面，配置一下图床信息，选择一下markdown文件或者文件夹地址就可以自动迁移了。后者是免费的，前者虽然收费但是有免费体验期，对于只使用一次的用户来说就是免费。

![iPic and iPic Mover](https://image.i-ll.cc//uPic/20211010/EvkeIl.png?imageMogr2/auto-orient/blur/1x0/quality/75|watermark/2/text/WmhhbyBDaGnigJhzIEJsb2c=/font/dGltZXMgbmV3IHJvbWFu/fontsize/240/fill/IzAwMDAwMA==/dissolve/75/gravity/SouthEast/dx/10/dy/10|imageslim)

~~实际上还有[PicGo](https://github.com/Molunerfinn/PicGo)和[picgo-plugin-pic-migrater](https://github.com/PicGo/picgo-plugin-pic-migrater)，可以使用。~~ 之前可能有用，但是程序很久都没有更新过了，一堆bug，根本不能正常迁移。还是推荐大家使用iPic和iPic Mover。

## 随便说说

服务器是2021年9月27日到期，由于我学习和工作太忙，一直抽不出时间来弄。就又将服务器续费了7天。抽空的时候研究一下怎么迁移最方便。直到2021年10月2号才完全弄好，今天才有一点时间将迁移过程总结一下。这个方案完美适配我自己的网站，不一定适合所有人，在此分享出迁移思路或许对大家有所帮助。(ps. 研究生期间没有怎么更新blog，PhD期间争取做到一到两周更一次，内容大概会聚焦在研究方向和大数据相关的知识上。)
