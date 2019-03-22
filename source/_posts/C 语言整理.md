---
title: C 语言整理
date: 2018-03-08 20:09:28
tags: C
categories: language
---
# C 语言整理
- [C 语言整理](#c-语言整理)
  - [数据类型](#数据类型)
    - [符号修饰符](#符号修饰符)
    - [存储修饰符](#存储修饰符)
    - [属性修饰符](#属性修饰符)
  - [分支条件](#分支条件)
  - [循环](#循环)
  - [函数](#函数)
  - [程序组织](#程序组织)
  - [编译](#编译)
  - [工具](#工具)
  - [C 语言标准](#c-语言标准)
  - [C 语言各平台实现](#c-语言各平台实现)

<!-- more -->

## 数据类型
+ char
+ short
+ int
+ long
+ float
+ double
+ enum
+ union
+ struct
+ 指针
+ 数组
+ typedef
  
### 符号修饰符
+ signed
+ unsigned
  
### 存储修饰符
`动态存储`
+ auto
+ register
  
`静态存储`    
+ static
+ extern

### 属性修饰符
+ const
+ violate


## 分支条件
+ if / else / elseif
+ switch / case / break
  
## 循环
+ for
+ while
+ do while


## 函数
+ 定义
+ 可变参数
+ 内联函数
+ 调用方式
  + __stdcall
  + __cdecl
  + __fastcall

## 程序组织
+ 头文件 #include
+ .c 文件
+ 库
  + 静态库 lib
  + 动态库 (dll/so)
    + linux so 命名规则
      + real name libname.so.x.y.z
      + so name  libname.so.x
      + link name  libname.so

## 编译
+ #define
+ #ifdef / #endif /#else / #else if
+ __FILE__ / __FUNCTION__ /__LINE__ / __DATE__ /__TIME__ 
+ #pragram message/ #pragram once /#pragram pack
+ #error 

## 工具
+ cmake
+ gcc
+ msbuild


## C 语言标准
+ ASCI C
+ POSIX C

## C 语言各平台实现
+ msvcrt.dll (windows)
+ glibc.so (linux)
