---
title: C++随手记
---

![编译期反射的作用](C:\Users\22953\Desktop\blog\img\编译期反射的作用.png)

https://codechina.gitcode.host/programmer/cpp-update/1-C++14-magic_get-and-pod





## 安装gcc和g++

天在linux的服务器上安装C/C++的编译器gcc和g++，运行了如下两条命令：

yum install gcc
yum install g++

　　然后发现gcc可以正确安装，但安装g++时却提示： Cannot find a package matching g++

　　后在网上搜索后才发现，原来在linux下，C++的编译器不是g++这个名称，而是gcc-c++，由此看来的确是我想当然了。然后直接运行

 yum install gcc-c++ libstdc++-devel
　　就可以了。安装完成后在linux下输入: which g++，就看到g++已经安装完成（一般是在 /usr/bin 目录下）

## 关键字

```c++
static const int a;//success
const static int b;//success
```

# 哈希表

**一般哈希表都是用来快速判断一个元素是否出现集合里**。

## 结构体嵌套初始化

 对普通类型int,char new后面添加（）自动初始化

对类来说，无论后面是否添加（）都会初始化，即对结构体同理
