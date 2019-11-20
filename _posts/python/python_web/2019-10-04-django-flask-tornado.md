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
```python
在线安装Django
pip3 install Django
检测当前是否安装Django及版本
python3 -m django --version
1.11.7
```
