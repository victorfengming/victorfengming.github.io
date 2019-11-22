---
title: "Django笔记01"
tags: Python solution web
---

# 浅谈Web框架
### 一,什么是框架?
软件框架就是为实现或完成某种软件开发时,提供了一些基础的软件产品,

框架的功能类似于基础设施,提供并实现最为基础的软件架构和体系

通常情况下我们依据框架来实现更为复杂的业务程序开发

一个字,框架就是程序的骨架

### 二,框架的优缺点
可重用

成熟,稳健

可扩展性良好

选对框架很重要

### 三,python中常见的框架
大包大揽 `Django` 被官方称之为完美主义者的Web框架。

力求精简 `web.py`和`Tornado`

新生代微框架 `Flask`和`Bottle`

### MVC设计模式
MVC实现了前后端和数据的分离,程序的解耦合,实现了程序的可扩展性,可维护性

|英文|中文|针对部分|作用|
|---|---|---|---|
| Model | 模型 | 是针对数据库层面的 | 程序调用模型,直接操作继承model的模型对象|
| View | 视图 | 是针对用户界面的数据显示 | 模板(hmtl)|
| Controller | 控制器 | 针对业务逻辑的操作 | python程序|

### MVT

|||||
|---|---|---|---|
|M|Model|模型|数据层|
|V|View|视图|业务逻辑|
|T|Template|模板|html|

# Django简介
### 1. 认识Django
Django是一个高级的Python Web框架，它鼓励快速开发和清洁，务实的设计。
由经验丰富的开发人员构建，它负责Web开发的许多麻烦，因此您可以专注于编写应用程序，而无需重新创建轮子。
它是免费的和开源的。
被官方称之为完美主义者的Web框架。
Django可以更快地构建更好的Web应用程序并减少代码。

官方网址：https://www.djangoproject.com/

中文文档:http://python.usyiyi.cn/

### 2. Django框架的特点：
快速开发：Django的宗旨在于帮助开发人员快速从概念到完成应用程序。
安全可靠：Django认真对待安全性，帮助开发人员避免许多常见的安全错误。
超可伸缩性: Web上的一些最繁忙的网站利用了Django快速灵活扩展的能力。


### 3. Django可以使用什么Python版本？

|Django版本	|Python版本|
|---|---|
|1.8|	2.7，3.2（直到2016年底），3.3, 3.4, 3.5|
|1.9, 1.10	|2.7, 3.4, 3.5|
|1.11	|2.7 , 3.4 , 3.5 , 3.6|
|2.0	|3.5+|
### 4. Django的开发版本
LTS : 长期稳定版
- 2015 April 1.8
- 2017 April 1.11
- 2019 April 2.2

### 5. Django安装
作为Python Web框架，Django需要Python，在安装Python同时需要安装pip。
```cmd
# 在线安装Django
pip3 install Django
# 检测当前是否安装Django及版本
python3 -m django --version
1.11.7
```
这里可以使用 -i 参数来指定镜像源位置

### 6. 使用Django框架搭建项目
```shell
# 在一个目录中执行一下命令,就会创建一个web项目目录
django-admin startproject web

# 进入到web文件夹中,执行以下命令,启动项目
python3 manage.py runserver

# 接下来就可以在浏览器中访问了

```
### 创建一个应用
```shell
python3 manage.py startapp home

# 以上命令会在项目文件夹中创建一个目录home
```

### 请求的流程
用户输入url地址发起请求,服务器接受到请求后,交给跟路由(项目同名目录下的urls.py)

### 使用模板文件

### 路由的定义
>URL ==> 统一资源定位符
>指得就是请求的(URL)地址
>http://python.itxdl.cn/html/tutorial/
>http://python.itxdl.cn/html/teachers/
>可以在项目中指定请求的url地址,来交给对应的试图函数进行解析

### 路由的特点
>路由就是在urls中进行规则的配置
>按照从上往下的顺序来执行
>如果匹配到,则假装指定的视图函数来执行
>如果匹配不到,则抛出404 page not found

### 路由参数
>路由参数就是在定义规则时,使用小括号`()`括起来的内容,将作为参数传递给视图函数
```python
# 路由规则
url(r'^article/(\d)$', views.article),
# 视图函数
def article(request,para):
    return HttpResponse('接受到的参数是:'+para)
```

### 命名组,命名参数
>和路由参数一样是用来获取url中路径作为参数来使用
>不同的是,命名组会把当前参数作为,关键字参数传递给视图函数,
>因此对应的视图函数,必须有关键字参数
```python
# 命名组 使用?P<变量名>方式来定义
url(r'abc/(?P<aa>[0-9]+/$',view.abc_2003)

# 在对应的视图函数中则必须有对应的关键字
def abc_2003(request,aa):
    print(aa)
    return HttpResponse('abc_2003')
```

### 指定用于视图参数的默认值
两个路由指向同一个视图函数
```python
# 路由
url(r'^user/index/(?P<page>[0-9]+)/$', views.user_index),
url(r'^user/index/$', views.user_index),

# 视图函数
def user_index(request,page=1):
    print(page)
    return HttpResponse('用户列表数据的显示'+page)    
```

### 数据库配置
1. 安装mysql
2. 创建库,指定字符集
3. 安装pymysql
4. 在settings.py的同级目录中找到__init__.py文件,声明pymysql
5. 在settings.py文件中配置 数据库
6. 在settings.py文件中添加当前的应用

### 定义模型
1. 找到应用中的models.py文件
```python
from django.db import models

# Create your models here.
# 模型的作用,降低程序的耦合性,更换数据库就改个配置文件就行了

class Users(models.Model):
    username = models.CharField(max_length=32)
    password = models.CharField(max_length=32)
    email = models.CharField(max_length=50)
```

2. 生成迁移文件
```shell
python3 manage.py makemigrations
```
3. 执行迁移
```shell
python3 manage.py makemigrate
```

### 在视图函数中使用模型
1. 先在视图函数中导入models
```python
from . import models
```
```python
# 模型的操作演示
def mod_demo(request):
    # 使用模型进行操作数据库 数据的查询操作
    res = models.Users.objects.all()
    print(res)
    # < QuerySet[ < Users: Users object >] >
    # 一个查询集
    for x in res:
        print(x.username)
    return HttpResponse('模型你给的操作演示')
```
