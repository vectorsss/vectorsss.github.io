---
title: "plsql连接Oracle数据库、解决plsql中文乱码、免注册在Oracle官网下载文件、Oracel  Database全套下载链接"
date: "2017-05-17"
categories: 
  - "database"
tags: 
  - "oracle"
  - "数据库"
url: "/archives/104"
---

## Plsql下载以及安装

- 第一个需要安装Oralce 客户端，第二个不需要，但是tsn文件得自己配置

![](https://image.i-ll.cc/2021-10-01-125352.png)  

image.png

- 下载地址如下

`链接: [https://pan.baidu.com/s/1dEK8o1r](https://pan.baidu.com/s/1dEK8o1r) 密码: bhpm`

- 文件一压缩包里面都有详细的安装说明，这里不再赘述。
- 文件二直接解压即可。  
    （二选一，第二个需要自己配置TSN文件）
    
    ### 安装Oracle并配置plsql里面的目录
    
    我自己安装的Oracle 11G和Oracle client是都是64位。  
    建议大家Oracle client安装32位的。  
    如果是64位Oracle client已经装好了的话。请看以下步骤：
- 需要的所有文件`(复制链接用迅雷下载)  
    [http://download.oracle.com/otn/nt/oracle11g/112010/win64_11gR2_client.zip](http://download.oracle.com/otn/nt/oracle11g/112010/win64_11gR2_client.zip)  
    [http://download.oracle.com/otn/nt/oracle11g/112010/win64_11gR2_database_2of2.zip](http://download.oracle.com/otn/nt/oracle11g/112010/win64_11gR2_database_2of2.zip)  
    [http://download.oracle.com/otn/nt/oracle11g/112010/win64_11gR2_database_1of2.zip](http://download.oracle.com/otn/nt/oracle11g/112010/win64_11gR2_database_1of2.zip)  
    [http://download.oracle.com/otn/nt/instantclient/112030/instantclient-basic-nt-11.2.0.3.0.zip](http://download.oracle.com/otn/nt/instantclient/112030/instantclient-basic-nt-11.2.0.3.0.zip)`
- 将win64\_11gR2 1of2和win64\_11gR2 2of2放到同一个目录下直接解压安装
- 安装win64\_11gR2\_client
- 解压instantclient-basic-nt-11.2.0.3.0.zip(随便解压到哪都行)
- 参考下图配置路径

![](https://image.i-ll.cc/2021-10-01-125354.png)  

image.png

### 添加环境变量

#### 解决plsql中文乱码问题

计算机->属性->高级系统设置->环境变量->新建系统变量  
变量名：NLS\_LANG  
变量值：SIMPLIFIED CHINESE\_CHINA.ZHS16GBK

#### 指向TNS文件所在目录

变量名：TNS\_ADMIN  
变量值：E:\\Oracle\\product\\11.2.0\\dbhome\_1\\NETWORK\\ADMIN

## Oracel配置数据库连接信息

- 打开Oracle Net Manager点+号新建就可以了，有的厂商提供SID的话这边就要单独按他们提供的来填写，否则会出现ORA-12541:无监听程序

![](https://image.i-ll.cc/2021-10-01-125358.png)  

image.png

- 打开plsql输入用户名密码，选择数据库即可正常登录

![](https://image.i-ll.cc/2021-10-01-125400.png)  

image.png

## Oracle官网免注册下载教程

- 先Decline License Agreement,然后鼠标选择要下载的文件
- 更改Decline License Agreement为 Accept License Agreement 下载地址就出来了  
    
    ![](https://image.i-ll.cc/2021-10-01-125403.png)  
    
    image.png
    

![](https://image.i-ll.cc/2021-10-01-125408.png)  

image.png

# Oracle全家桶下载地址(不定时更新，所有文件都直接复制到迅雷下载)

`Oracle Database 11g Release 2 (11.2.0.1.0) for Microsoft Windows (64-bit)`

[http://download.oracle.com/otn/nt/oracle11g/112010/win64\_11gR2\_database\_1of2.zip](http://download.oracle.com/otn/nt/oracle11g/112010/win64_11gR2_database_1of2.zip)

[http://download.oracle.com/otn/nt/oracle11g/112010/win64\_11gR2\_database\_2of2.zip](http://download.oracle.com/otn/nt/oracle11g/112010/win64_11gR2_database_2of2.zip)

[http://download.oracle.com/otn/nt/oracle11g/112010/win64\_11gR2\_client.zip](http://download.oracle.com/otn/nt/oracle11g/112010/win64_11gR2_client.zip)

[http://download.oracle.com/otn/nt/oracle11g/112010/win64\_11gR2\_grid.zip](http://download.oracle.com/otn/nt/oracle11g/112010/win64_11gR2_grid.zip)

Oracle Database 11g Release 2 (11.2.0.1.0) for Microsoft Windows (32-bit)

[http://download.oracle.com/otn/nt/oracle11g/112010/win32\_11gR2\_database\_1of2.zip](http://download.oracle.com/otn/nt/oracle11g/112010/win32_11gR2_database_1of2.zip)

[http://download.oracle.com/otn/nt/oracle11g/112010/win32\_11gR2\_database\_2of2.zip](http://download.oracle.com/otn/nt/oracle11g/112010/win32_11gR2_database_2of2.zip)

[http://download.oracle.com/otn/nt/oracle11g/112010/win32\_11gR2\_client.zip](http://download.oracle.com/otn/nt/oracle11g/112010/win32_11gR2_client.zip)

Oracle Database 11g Release 2 (11.2.0.1.0) for Linux x86

[http://download.oracle.com/otn/linux/oracle11g/R2/linux\_11gR2\_database\_1of2.zip](http://download.oracle.com/otn/linux/oracle11g/R2/linux_11gR2_database_1of2.zip)

[http://download.oracle.com/otn/linux/oracle11g/R2/linux\_11gR2\_database\_2of2.zip](http://download.oracle.com/otn/linux/oracle11g/R2/linux_11gR2_database_2of2.zip)

[http://download.oracle.com/otn/linux/oracle11g/R2/linux\_11gR2\_client.zip](http://download.oracle.com/otn/linux/oracle11g/R2/linux_11gR2_client.zip)

[http://download.oracle.com/otn/linux/oracle11g/R2/linux\_11gR2\_grid.zip](http://download.oracle.com/otn/linux/oracle11g/R2/linux_11gR2_grid.zip)

Oracle Database 11g Release 2 (11.2.0.1.0) for Linux x86-64

[http://download.oracle.com/otn/linux/oracle11g/R2/linux.x64\_11gR2\_database\_1of2.zip](http://download.oracle.com/otn/linux/oracle11g/R2/linux.x64_11gR2_database_1of2.zip)

[http://download.oracle.com/otn/linux/oracle11g/R2/linux.x64\_11gR2\_database\_2of2.zip](http://download.oracle.com/otn/linux/oracle11g/R2/linux.x64_11gR2_database_2of2.zip)

[http://download.oracle.com/otn/linux/oracle11g/R2/linux.x64\_11gR2\_client.zip](http://download.oracle.com/otn/linux/oracle11g/R2/linux.x64_11gR2_client.zip)

[http://download.oracle.com/otn/linux/oracle11g/R2/linux.x64\_11gR2\_grid.zip](http://download.oracle.com/otn/linux/oracle11g/R2/linux.x64_11gR2_grid.zip)

Oracle Database 11g Release 2 (11.2.0.1.0) for Solaris Operating System (SPARC) (64-bit)

[http://download.oracle.com/otn/solaris/oracle11g/R2/solaris.sparc64\_11gR2\_database\_1of2.zip](http://download.oracle.com/otn/solaris/oracle11g/R2/solaris.sparc64_11gR2_database_1of2.zip)

[http://download.oracle.com/otn/solaris/oracle11g/R2/solaris.sparc64\_11gR2\_database\_2of2.zip](http://download.oracle.com/otn/solaris/oracle11g/R2/solaris.sparc64_11gR2_database_2of2.zip)

[http://download.oracle.com/otn/solaris/oracle11g/R2/solaris.sparc64\_11gR2\_client.zip](http://download.oracle.com/otn/solaris/oracle11g/R2/solaris.sparc64_11gR2_client.zip)

[http://download.oracle.com/otn/solaris/oracle11g/R2/solaris.sparc64\_11gR2\_client32.zip](http://download.oracle.com/otn/solaris/oracle11g/R2/solaris.sparc64_11gR2_client32.zip)

[http://download.oracle.com/otn/solaris/oracle11g/R2/solaris.sparc64\_11gR2\_grid.zip](http://download.oracle.com/otn/solaris/oracle11g/R2/solaris.sparc64_11gR2_grid.zip)

Oracle Database 11g Release 2 (11.2.0.1.0) for Solaris Operating System (x86-64)

[http://download.oracle.com/otn/solaris/oracle11g/R2/solaris.x64\_11gR2\_database\_1of2.zip](http://download.oracle.com/otn/solaris/oracle11g/R2/solaris.x64_11gR2_database_1of2.zip)

[http://download.oracle.com/otn/solaris/oracle11g/R2/solaris.x64\_11gR2\_database\_2of2.zip](http://download.oracle.com/otn/solaris/oracle11g/R2/solaris.x64_11gR2_database_2of2.zip)

[http://download.oracle.com/otn/solaris/oracle11g/R2/solaris.x64\_11gR2\_client.zip](http://download.oracle.com/otn/solaris/oracle11g/R2/solaris.x64_11gR2_client.zip)

[http://download.oracle.com/otn/solaris/oracle11g/R2/solaris.x86\_11gR2\_client.zip](http://download.oracle.com/otn/solaris/oracle11g/R2/solaris.x86_11gR2_client.zip)

[http://download.oracle.com/otn/solaris/oracle11g/R2/solaris.x64\_11gR2\_grid.zip](http://download.oracle.com/otn/solaris/oracle11g/R2/solaris.x64_11gR2_grid.zip)

Oracle Database 11g Release 2 (11.2.0.1.0) for HP-UX Itanium

[http://download.oracle.com/otn/hp/oracle11g/R2/hpia64\_11gR2\_database\_1of2.zip](http://download.oracle.com/otn/hp/oracle11g/R2/hpia64_11gR2_database_1of2.zip)

[http://download.oracle.com/otn/hp/oracle11g/R2/hpia64\_11gR2\_database\_2of2.zip](http://download.oracle.com/otn/hp/oracle11g/R2/hpia64_11gR2_database_2of2.zip)

[http://download.oracle.com/otn/hp/oracle11g/R2/hpia64\_11gR2\_client.zip](http://download.oracle.com/otn/hp/oracle11g/R2/hpia64_11gR2_client.zip)

[http://download.oracle.com/otn/hp/oracle11g/R2/hpia64\_11gR2\_client32.zip](http://download.oracle.com/otn/hp/oracle11g/R2/hpia64_11gR2_client32.zip)

[http://download.oracle.com/otn/hp/oracle11g/R2/hpia64\_11gR2\_grid.zip](http://download.oracle.com/otn/hp/oracle11g/R2/hpia64_11gR2_grid.zip)

Oracle Database 11g Release 2 (11.2.0.1.0) for HP-UX PA-RISC (64-bit)

[http://download.oracle.com/otn/hp/oracle11g/R2/hpux.parisc64\_11gR2\_database\_1of2.zip](http://download.oracle.com/otn/hp/oracle11g/R2/hpux.parisc64_11gR2_database_1of2.zip)

[http://download.oracle.com/otn/hp/oracle11g/R2/hpux.parisc64\_11gR2\_database\_2of2.zip](http://download.oracle.com/otn/hp/oracle11g/R2/hpux.parisc64_11gR2_database_2of2.zip)

[http://download.oracle.com/otn/hp/oracle11g/R2/hpux.parisc64\_11gR2\_client.zip](http://download.oracle.com/otn/hp/oracle11g/R2/hpux.parisc64_11gR2_client.zip)

[http://download.oracle.com/otn/hp/oracle11g/R2/hpux.parisc32\_11gR2\_client.zip](http://download.oracle.com/otn/hp/oracle11g/R2/hpux.parisc32_11gR2_client.zip)

[http://download.oracle.com/otn/hp/oracle11g/R2/hpux.parisc64\_11gR2\_grid.zip](http://download.oracle.com/otn/hp/oracle11g/R2/hpux.parisc64_11gR2_grid.zip)

Oracle Database 11g Release 2 (11.2.0.1.0) for AIX (PPC64)

[http://download.oracle.com/otn/aix/oracle11g/R2/aix.ppc64\_11gR2\_database\_1of2.zip](http://download.oracle.com/otn/aix/oracle11g/R2/aix.ppc64_11gR2_database_1of2.zip)

[http://download.oracle.com/otn/aix/oracle11g/R2/aix.ppc64\_11gR2\_database\_2of2.zip](http://download.oracle.com/otn/aix/oracle11g/R2/aix.ppc64_11gR2_database_2of2.zip)

[http://download.oracle.com/otn/aix/oracle11g/R2/aix.ppc64\_11gR2\_client.zip](http://download.oracle.com/otn/aix/oracle11g/R2/aix.ppc64_11gR2_client.zip)

[http://download.oracle.com/otn/aix/oracle11g/R2/aix.ppc32\_11gR2\_client.zip](http://download.oracle.com/otn/aix/oracle11g/R2/aix.ppc32_11gR2_client.zip)

[http://download.oracle.com/otn/aix/oracle11g/R2/aix.ppc64\_11gR2\_grid.zip](http://download.oracle.com/otn/aix/oracle11g/R2/aix.ppc64_11gR2_grid.zip)

ORACLE10GR2

Oracle Database 10g Release 2 (10.2.0.1.0) Enterprise/Standard Edition for Microsoft Windows (32-bit)

[http://download.oracle.com/otn/nt/oracle10g/10201/10201\_database\_win32.zip](http://download.oracle.com/otn/nt/oracle10g/10201/10201_database_win32.zip)  
[http://download.oracle.com/otn/nt/oracle10g/10201/10201\_client\_win32.zip](http://download.oracle.com/otn/nt/oracle10g/10201/10201_client_win32.zip)  
[http://download.oracle.com/otn/nt/oracle10g/10201/10201\_clusterware\_win32.zip](http://download.oracle.com/otn/nt/oracle10g/10201/10201_clusterware_win32.zip)  
[http://download.oracle.com/otn/nt/oracle10g/10201/10201\_gateways\_win32.zip](http://download.oracle.com/otn/nt/oracle10g/10201/10201_gateways_win32.zip)

Oracle Database 10g Release 2 (10.2.0.1.0) Enterprise/Standard Edition for Microsoft Windows (x64)

[http://download.oracle.com/otn/nt/oracle10g/10201/102010\_win64\_x64\_database.zip](http://download.oracle.com/otn/nt/oracle10g/10201/102010_win64_x64_database.zip)  
[http://download.oracle.com/otn/nt/oracle10g/10201/102010\_win64\_x64\_client.zip](http://download.oracle.com/otn/nt/oracle10g/10201/102010_win64_x64_client.zip)  
[http://download.oracle.com/otn/nt/oracle10g/10201/102010\_win64\_x64\_clusterware.zip](http://download.oracle.com/otn/nt/oracle10g/10201/102010_win64_x64_clusterware.zip)

Oracle Database 10g Release 2 (10.2.0.1.0) Enterprise/Standard Edition for Linux x86

[http://download.oracle.com/otn/linux/oracle10g/10201/10201\_database\_linux32.zip](http://download.oracle.com/otn/linux/oracle10g/10201/10201_database_linux32.zip)  
[http://download.oracle.com/otn/linux/oracle10g/10201/10201\_client\_linux32.zip](http://download.oracle.com/otn/linux/oracle10g/10201/10201_client_linux32.zip)  
[http://download.oracle.com/otn/linux/oracle10g/10201/10201\_gateways\_linux32.zip](http://download.oracle.com/otn/linux/oracle10g/10201/10201_gateways_linux32.zip)

Oracle Database 10g Release 2 (10.2.0.1.0) Enterprise/Standard Edition for Linux x86-64

[http://download.oracle.com/otn/linux/oracle10g/10201/10201\_database\_linux\_x86\_64.cpio.gz](http://download.oracle.com/otn/linux/oracle10g/10201/10201_database_linux_x86_64.cpio.gz)  
[http://download.oracle.com/otn/linux/oracle10g/10201/10201\_client\_linux\_x86\_64.cpio.gz](http://download.oracle.com/otn/linux/oracle10g/10201/10201_client_linux_x86_64.cpio.gz)  
[http://download.oracle.com/otn/linux/oracle10g/10201/10201\_clusterware\_linux\_x86\_64.cpio.gz](http://download.oracle.com/otn/linux/oracle10g/10201/10201_clusterware_linux_x86_64.cpio.gz)  
[http://download.oracle.com/otn/linux/oracle10g/10201/10201\_gateways\_linux\_x86\_64.cpio.gz](http://download.oracle.com/otn/linux/oracle10g/10201/10201_gateways_linux_x86_64.cpio.gz)

Oracle Database 10g Release 2 (10.2.0.1.0) Enterprise/Standard Edition for AIX5L

[http://download.oracle.com/otn/aix/oracle10g/10201/10gr2\_aix5l64\_database.cpio.gz](http://download.oracle.com/otn/aix/oracle10g/10201/10gr2_aix5l64_database.cpio.gz)  
[http://download.oracle.com/otn/aix/oracle10g/10201/10gr2\_aix5l64\_client.cpio.gz](http://download.oracle.com/otn/aix/oracle10g/10201/10gr2_aix5l64_client.cpio.gz)  
[http://download.oracle.com/otn/aix/oracle10g/10201/10gr2\_aix5l64\_cluster.cpio.gz](http://download.oracle.com/otn/aix/oracle10g/10201/10gr2_aix5l64_cluster.cpio.gz)  
[http://download.oracle.com/otn/aix/oracle10g/10201/10gr2\_aix5l64\_gateways.cpio.gz](http://download.oracle.com/otn/aix/oracle10g/10201/10gr2_aix5l64_gateways.cpio.gz)

Oracle Database 10g Release 2 (10.2.0.2) Enterprise/Standard Edition for Solaris Operating System (x86)

[http://download.oracle.com/otn/solaris/oracle10g/10202/10202\_database\_solx86.zip](http://download.oracle.com/otn/solaris/oracle10g/10202/10202_database_solx86.zip)  
[http://download.oracle.com/otn/solaris/oracle10g/10202/10202\_client\_solx86.zip](http://download.oracle.com/otn/solaris/oracle10g/10202/10202_client_solx86.zip)  
[http://download.oracle.com/otn/solaris/oracle10g/10202/10202\_clusterware\_solx86.zip](http://download.oracle.com/otn/solaris/oracle10g/10202/10202_clusterware_solx86.zip)

Oracle Database 10g Release 2 (10.2.0.1.0) Enterprise/Standard Edition for Solaris Operating System (x86-64)

[http://download.oracle.com/otn/solaris/oracle10g/10201/x8664/10201\_database\_solx86\_64.zip](http://download.oracle.com/otn/solaris/oracle10g/10201/x8664/10201_database_solx86_64.zip)  
[http://download.oracle.com/otn/solaris/oracle10g/10201/x8664/10201\_client\_solx86\_64.zip](http://download.oracle.com/otn/solaris/oracle10g/10201/x8664/10201_client_solx86_64.zip)  
[http://download.oracle.com/otn/solaris/oracle10g/10201/x8664/10201\_clusterware\_solx86\_64.zip](http://download.oracle.com/otn/solaris/oracle10g/10201/x8664/10201_clusterware_solx86_64.zip)
