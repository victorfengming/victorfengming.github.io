---
title: "Python面试题"
subtitle: "个人整理"
tags: Python background interview
---





* content
{:toc}




### 关于一个内容的四个分析角度
- 是什么?
- 能干什么?
- 怎么用?
- 优缺点?

### 学过Django么
[Django笔记01-基础](https://victorfengming.gitee.io/victorfengming_old/2019/11/23/django-note1/)  
[Django/Flask/Tornado三大web框架性能分析](https://victorfengming.gitee.io/victorfengming_old/2019/10/04/django-flask-tornado/)

### 你会正则表达式么?
- 分析
    - 是什么?
    - 能干什么?
    - 怎么用?
    - 优缺点?
- 我对正则表达式的理解是:
    - 使用字符串,转义字符串,元字符来定义一个规则,去匹配或者搜索一个指定的内容,获取符合要求的内容
    - 比如我们在js中使用正则来监测用户输入的信息是否正确
    - 或我们在爬虫中使用正则来爬取我们想要的数据和内容
    - 我们在爬虫中除了使用正则外还可以使用xpath等方法来获取数据内容,更方便
- 以上就是我对正则表达式的理解
    
### 你对mysql的理解    
[Mysql数据库简介](https://victorfengming.gitee.io/victorfengming_old/2019/09/27/mysql-introduce/)

### char varchar text 区别
首先都是mysql中的字符串类型
char 定长字符串(比如,密码因为都是加密后长度一样的)
varchar 变长字符串(节省空间)
text 大篇幅的文章文本(效率低,不能设置不默认值)