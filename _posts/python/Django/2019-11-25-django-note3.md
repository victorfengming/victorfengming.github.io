---
title: "Django笔记-模板引擎"
subtitle: "重量级选手中最有代表性的一位"
tags: Python solution web
---



* content
{:toc}





# 模板引擎
# CSRF攻击
# 自定义过滤/器
1. 在应用中创建一个templatetags文件夹
2. 在templatetags 包中定义一个模块文件diytags.py
```python
from django import template

register = template.Library()

# 自定义过滤器
@register.filter
def yc_upper(val):
    return val.upper()


# 自定义标签
from django.utils.html import format_html
@register.simple_tag
def jia(a,b):
    res = int(a) + int(b)
    return res

```
3. 在需要使用的模板中, 导入自定义的模块