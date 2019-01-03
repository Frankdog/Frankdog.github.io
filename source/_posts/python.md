---
title: python
date: 2018-12-19 09:48:36
tags: python
categories: python
---
- [functional program](#functional-program)
  - [decorator](#decorator)
    - [无参数 decorator](#无参数-decorator)
    - [带参数的decorator](#带参数的decorator)
  - [partial function](#partial-function)
- [test](#test)
  - [doctest](#doctest)
  - [uinit test](#uinit-test)

<!-- more -->

# functional program
## decorator
### 无参数 decorator
```python
import functools

def log(func):
    @functools.wraps(func)
    def wrapper(*args,**kw):
        print('call %s()'%func.__name__)
        return func(*args,**kw)
    return wrapper

@log
def add(a,b)
    return a+b
```
### 带参数的decorator
```python
import functools

def log(func):
    @functools.wraps(func)
    def wrapper(*args,**kw):
        print('%s %s()'%(text,func.__name__))
        return func(*args,**kw)
    return wrapper

@log('abc')
def add(a,b):
    return a+b
```
## partial function
>简单总结`functools.partial`的作用就是，把一个函数的某些参数给固定住（也就是设置默认值），返回一个新的函数
```python
import functools
int2 = functools.partial(int,base=2)
```

# test
## doctest

 ```python
 '''
 >>> add(1,2)
 3
 '''
 def add(a,b):
    return a+b

if __name__ == "__main__":
    import doctest
    doctest.testmod()
 ```

## uinit test
 
 ```python
 def add(a,b):
    return a+b

if __name__ == "__main__":
    import unittest
  
    class Testadd(unittest.TestCase):
        def test_add(self):
            self.assertEqual(add(2,3),5)
        
    unittest.main()
 ```
