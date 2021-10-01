---
title: "Sublime MinGw实现C/C++代码编译运行"
date: "2017-07-05"
categories: 
  - "工具-效率"
tags: 
  - "工具-效率"
url: "/archives/97"
---

# 安装配置MinGw

## 下载安装MinGW

去官网下载MinGw ：[http://www.mingw.org/](http://www.mingw.org/)  
或者下载我已经下载好的完整版：[http://pan.baidu.com/s/1gfgluin](http://pan.baidu.com/s/1gfgluin) (2017.7.5更新)

![](https://image.i-ll.cc/2021-10-01-125409.png)  

如图所示

- 官网下载的选好后 Installation > Apply Changes 等待安装完成开始配置环境变量
- 选择离线版的直接解压到C盘根目录 开始配置环境变量
    
    ## 配置C/C++环境变量：
    
    ```
    - 变量名                     变量值
    - C_INCLUDEDE_PATH       C:\MinGW\include 
    - LIBRARY_PATH           C:\MinGW\lib 
    - Path                   C:\MinGW\bin
    ```
    

![](https://image.i-ll.cc/2021-10-01-125414.png)  

配置环境变量

## 测试MinGW是否配置成功

在桌面新建test.c文件

```
#include

int main()
{
    printf("hello\n");
    return 0;
}
```

打开控制台cd进入桌面

![](https://image.i-ll.cc/2021-10-01-125417.png)  

运行前

![](https://image.i-ll.cc/2021-10-01-125425.png)  

运行后

# Sublime Text3配置

工具->编译系统->编译新系统->复制下面代码进去  
`ctrl+s保存为C.sublime-build`

```
{
    "working_dir": "$file_path",
    "cmd": "gcc -Wall \"$file_name\" -o \"$file_base_name\"",
    "file_regex": "^(..[^:]*):([0-9]+):?([0-9]+)?:? (.*)$",
    "selector": "source.c",

    "variants": 
    [
        {    
        "name": "Run",
            "shell_cmd": "gcc -Wall \"$file\" -o \"$file_base_name\" && start cmd /c \"\"${file_path}/${file_base_name}\" & pause\""
        }
    ]
}
```

## 测试是否配置成功

工具->编译系统->选C

> ctrl+shift+b

编译运行

![](https://image.i-ll.cc/2021-10-01-125430.png)  

运行结果
