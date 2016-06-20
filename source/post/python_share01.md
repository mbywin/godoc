```toml

title = "Python分享-01"
slug = "2016"
date = "2016-06-19 18:49:59"
author = "miaoboyong"
tags = ["python"]

```
---
###__特点:__

1. 简单易学
2. 高层语言
3. 可移植性
4. 面向对象
5. ___丰富的库___(pandas，numpy等)
6. ___强制缩进___

###__争议:__
1. ___运行速度___
>![运行速度](/media/0 "运行速度")
2. ___源码部署___
>![源码部署](/media/1 "源码部署")
3. 多线程(GIL,全局解释器锁)
4. 框架选择太多

###__Python2和Python3:__###
1. future模块（__future__）
2. print 函数
3. 整除
4. Unicode
5. xrange
6. Raising exceptions
7. Handling exceptions
8. next() 函数 and .next() 方法
9. 比较不可排序类型
10. 返回可迭代对象，而不是列表

###__模块安装:__###
1. 源码安装  
   *python setup.py install*  
2. easy_install  
   *yum install python-setuptools*  
   *easy_install flask=={version}>*  
3. pip  
   *pip install flask=={version}*  
   *pip install -r requirement.txt*

###__开发工具:__
1. ___Pycharm___, Eclipse with PyDev
2. ___Sublime___, vim, emacs

###__Web框架:__
1. ___django___
2. ___tornado___
3. flask
4. webpy

### __协程框架__
1. ___gevent___
2. tornado
3. asyncio(异步IO，仅python3.4以上版本支持)

*[Python 中的进程、线程、协程、同步、异步、回调](https://segmentfault.com/a/1190000001813992 "协程")*

### __异步任务队列__
1. celery  
*消息代理*
>- *RabbitMQ*·
>- *redis*  

*Celery本身不含消息服务，它使用第三方消息服务来传递任务，目前，Celery支持的消息服务有RabbitMQ、Redis甚至是数据库，当然Redis应该是最佳选择。*

### __部署__
___gunicorn + supervisor + virtualenv___(*python 项目部署难度高*)

<!--python-->
