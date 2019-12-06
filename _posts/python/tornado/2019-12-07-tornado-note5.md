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