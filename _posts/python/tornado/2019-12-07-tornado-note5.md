---
title: "tornado学习笔记day05"
subtitle: "小而精的python web框架"
tags: Python solution web tornado
---



* content
{:toc}





# 模板

## 配置模板路径
这个在之前我们已经配置好了,可以参考前面的文章
```python
settings = {
    # 就像upfile就没有,你写了也白扯
    'template_path': os.path.join(BASE_DIR, "templates"),
}
```
## 渲染并返回给客户端

使用render()方法

```python
class HomeIndexHandler(RequestHandler):
    def get(self):
        self.render("home.html")
```
## 变量与表达式

### 语法
- { { var } }
- { { expression } }
### 实例
```python
class HomeIndexHandler(RequestHandler):
    def get(self):
        temp = 100
        # 直接传一个变量就行
        self.render("home.html",num = temp)
        # self.render("home.html")
```

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>主页</title>
</head>
<body>
   <h1>这里是主页</h1>
   { { num } }
   <br>
   <!-- 这里支持加减  -->
   { { num + 1 } }
   { { num + 18 } }

   <!-- 这里需要用模板的注释才能真正的注释掉双大括号 -->
   <!-- 这里一定要注意,这个普通的注释会被加载到页面中 -->
   {# num: { { num } } #}
   <!-- 模板的注释才是真正的注释 -->
   {# num: {{ num + 10 }} #}
   <!-- 等号的赋值的不好使的,会报错  -->
   {# num: {{ num = 5}} #}
</body>
</html>
```

## 流程控制
### if
#### 格式
单个的if
```angular2html
{ % if表达式 % }
语句
{ % end %}
```
if和else的
```angular2html
{ % if表达式 % }
语句1
{ % else % }
语句2
{ % end %}
```
多个if 的

```angular2html
{ % if表达式1 % }
语句1
{ % elif 表达式2% }
语句2
{ % elif 表达式3% }
语句3
<!--这里面else可有可无-->
{ % end % }
```
#### 实例
```angular2html
{% if flag == 0%}
flag确实是0
{% elif flag == 0 %}
语句2
{% elif flag == 2 %}
flag bug
{% else %}
baiche
{% end %}
```
### for
这里面需要注意的是,结束模板语法都是` { % end % }`
```angular2html
{ % for 变量 in 集合 % }
语句
{ % end % }
```
实例:
```angular2html
<ul>
    {% for stu in stus %}
    <li>{{ stu }}</li>
    {% end %}
</ul>
```
### while
这个while很少使用,就不写了


## 函数 
### static_url()
#### 作用
- 获取配置中的静态目录的路径
- 将参数拼接到静态目录后面并返回新的路径
#### 示例
```angular2html
<link rel="stylesheet" href="{ { static_url('css/home.css') } }">
```
#### 优点
- 修改目录的话 只需要修改配置文件中的内容即可,不需要修改各种页面中的URL
- Hash值
    - static_url创建了基于文件内容的Hash值
    - 将其添加到文件的末尾(当一个查询参数)
    - 这个hash值总能够保证,我们每一次加载最新的版本
    - 而不是之前的缓存的版本
    - 不论是开发阶段还是线上阶段,都是很有必要的

## 转义
tornado默认开启自动转义功能,能够防止网站攻击
```python
class TranHandler(RequestHandler):
    def get(self):
        str = "<h1>能不能转义就看这会的了</h1>"
        self.render("trans.html",str = str)
```

```angular2html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>转义</title>
</head>
<body>
{{str}}
</body>
</html>
```
页面这样显示
```
<h1>能不能转义就看这会的了</h1>
```
### 关闭自动转义
- raw:`{ % raw str % }`这个会关闭一行
- 在页面模板中修改
    - autoescape:`{ % autoescape None % }`
    - 这个不管你三七二十一都关闭了就
- 在配置文件中修改 
    - `autoescape : None` 
    - 当为None时关闭当前项目的自动转义
- escape()函数
    - 这个函数能够在全局转义的条件下再不转义
    - `{{ escape(str) }}`    
    
## 继承
## 静态文件
- static_path
    - 作用
        - 告诉tornado从文件系统中某一个特定的位置提供我们的静态文件
    - 示例:`'static_path': os.path.join(BASE_DIR, "static"),`
    - 请求方式:`http://127.0.0.1:8080/static/html/index.html`
    - 引用其他文件:
    ```angular2html
    <link rel="stylesheet" href="{ {static_url('css/index.css')} }">
    <script src="{ {static_url('js/jquery.js')} }"></script>
    ```
    
- StaticFileHandler 
    - 使用原因:这种请求方式:`http://127.0.0.1:8080/static/html/index.html`对于用户来说,体验不佳
    - 本质: 是tornado预制的用来提供静态资源文件的Handler
    - 作用: 可以通过StaticFileHandler来映射静态资源文件
    - 使用:
        - 第一种写法
        ```python
        (r"/(.*)$", tornado.web.StaticFileHandler,{
                        "path":os.path.join(BASE_DIR,"static/html"),
                    }),
        ```
        - 第二种:
        ```python
        (
            r"/(.*)$",
            tornado.web.StaticFileHandler,
            {
                "path": os.path.join(BASE_DIR, "static/html"),
                "default_filename": "index.html"
            }
        ),
        ``` 
 
