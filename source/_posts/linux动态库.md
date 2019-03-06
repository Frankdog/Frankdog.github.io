---
title: linux动态库
date: 2019-01-22 21:59:07
tags: linux
categories: linux
---

# linux 动态库命名规则
lib`name`.so.`x`.`y`.`z`
|Field|含义| 作用| 
|:-   |:-:|:-|
| name| lib库名字|  |
| x   | 主版本号 | 不同的版本号之间不兼容|
| y   | 次版本号 |增量升级 向后兼容|
| z   | release 版本号|对应次版本的错误修正和性能提升，不影响兼容性|

# 动态库软连接
- realname
- soname
- linkname

# 
