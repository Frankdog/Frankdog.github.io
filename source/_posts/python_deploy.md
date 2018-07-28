---
title: python-deploy
date: 2018-03-22 21:17:25
tags: python
---
# python deploy

`nginx->guincorn->gevent->flask`

## fabric
> ssh based auto deploy tool
+ install fabric  
`pip install fabric`

+ Create a file named `fabfile.py`
```python
from fabric import *
env.user='denghh'
env.password='123456'
env.key_filename='/path/cert.pem'

def deploy():
    run('ls -l')
```
+ Excute command 
`fab deploy`

## nginx
> load balance

## guicorn
> WSGI

## gevent
> async


## flask
> web framework