---
title: javascript笔记
date: 2017-03-01 22:09:28
tags: javascript
categories: web
---

- [javascript](#javascript)
  - [数据类型(typeof)](#数据类型typeof)
  - [Object](#object)
  - [循环](#循环)
  - [iterable](#iterable)
  - [function](#function)
  - [变量作用域](#变量作用域)
    - [BOM](#bom)
  - [function](#function-1)
  - [对象](#对象)
  - [闭包](#闭包)
  - [异步编程方案](#异步编程方案)
  - [Promise](#promise)

<!-- more -->

# javascript
## 数据类型(typeof)
+ boolean
+ Number
+ String
+ Function (1.普通函数 2.构造函数)
+ Object
+ null
+ undefined

<!-- more -->

## Object
+ object["key"]
+ in (可能继承而来) 
+ hasOwnProperty(此对象定义)


## 循环
+ for var in objs (javacript/python)  
+ for i:num (java)
+ arr.forEach()


## iterable
+ array
+ Map(es6 key可以不为字符串)
+ Set


## function
+ arguments
+ ...rest(es6)


## 变量作用域
+ 局部作用域
+ 全局作用域(BOM window对象属性)  
+ 块级作用域( let )
+ 常量 const

### BOM
+ window
+ window.screen
+ window.location
+ windows.history  


## function
+ apply
+ call

## 对象
+ 方法1  
```javascript
var a={
    "name":"xiaoming"
};

```
+ 方法2
```
//构造函数
function student(){
    this.name = "xiaoming";        
}

student.prototype.hello=function(){
    console.log("hello");
}
var a = new student();
```
+ 原型继承
    - javascript 通过构造函数来生成实例
    - 构造函数本身也是一个对象
    - 构造函数包含一个prototype属性
    - protoype 属性也是一个对象

## 闭包

## 异步编程方案
+ callback
+ listener
+ pub/sub
+ promise (es6)
+ generator/async/await (es7)


## Promise
+ 串行执行回调
+ Promise.all(p1,p2) 并行执行获得p1,p2结果
+ Promise.race(p1,p2) 并行执行获得p1,p2先执行完的结果 
```
function test(resolve,reject){
    if(success){
        resolve(result);
    }else{
        reject(result);
    }
}
function success(result){
    console.log(result);
}

function error(result){
    console.log(result);
}

var p = new Promise(test);

p.then(success).catch(error);
```


