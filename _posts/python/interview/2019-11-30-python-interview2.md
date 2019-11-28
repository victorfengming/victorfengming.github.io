---
title: "Python 最常见的 170 道面试题全解析：2019 版(答案收集)"
subtitle: "全是干货分享"
tags: Python solution interview
---






* content
{:toc}






<h3 style="color:inherit;line-height:inherit;font-weight:bold;border-bottom:2px solid rgb(239,112,96);font-size:1.3em;" id="-1"><span style="font-size:inherit;line-height:inherit;font-weight:normal;background:rgb(239,112,96);color:rgb(255,255,255);">语言特性</span><span style="vertical-align:bottom;border-bottom:36px solid rgb(239,235,233);border-right:20px solid transparent;"> </span><a class="anchorjs-link " href="#-1" aria-label="Anchor link for:  1" data-anchorjs-icon="#" style="opacity: 1; padding-left: 0.375em;"></a></h3>

### 1.谈谈对 Python 和其他语言的区别:
答：Python 是一门语法简洁优美,功能强大无比,应用领域非常广泛,具有强大完备的第三方库，他是一门强类型的可移植、可扩展，可嵌入的解释型编程语言，属于动态语言。

拿 C 语言和 Python 比： Python 的第三方类库比较齐全并且使用简洁,很少代码就能实现一些功能，如果用 C 去实现相同的功能可能就比较复杂。

但是对于速度来说 Python 的运行速度相较于 C 就比较慢了。

所以有利的同时也有弊端，毕竟我们的学习成本降低了。

如需了解更多,你还可以去看[详情](https://victorfengming.github.io/2019/11/28/python-feature/)

### 2.简述解释型和编译型编程语言:
解释型语言是在运行程序的时候才翻译，每执行一行，要翻译一行，边翻译边执行，效率较低。 

编译型就是直接编译成机型可以执行的，只翻译一次，所以效率相对来说较高。

如需了解更多,你还可以去看[详情](https://victorfengming.github.io/2019/11/28/compile-explain/)


### 3.Python 的解释器种类以及相关特点？
CPython c 语言开发的，使用最广的解释器

IPython 基于 cPython 之上的一个交互式计时器，交互方式增强功能和 cPython 一样

PyPy 目标是执行效率，采用 JIT 技术。对 Python 代码进行动态编译，提高执行效率

JPython 运行在 Java 上的解释器，直接把 Python 代码编译成 Java 字节码执行

IronPython 运行在微软 .NET 平台上的解释器，把 Python 编译成 . NET 的字节码。

如需了解更多,你还可以去看[详情](https://victorfengming.github.io/2019/11/28/interpreter-type/)

### 4.说说你知道的Python3 和 Python2 之间的区别？
print 在 Python3 中是函数必须加括号，Python2 中 print 为 class。

Python2 中使用 xrange，Python3 使用 range。

Python2 中默认的字符串类型默认是 ASCII，Python3 中默认的字符串类型是 Unicode。

Python2 中/的结果是整型，Python3 中是浮点类型。

Python2 中声明元类：metaclass = MetaClass,Python3 中声明元类：class newclass(metaclass=MetaClass)：pass。

如需了解更多,你还可以去看[详情](https://victorfengming.github.io/2019/11/28/python2-python3/)

### 5.Python3 和 Python2 中 int 和 long 区别？
python2中有int(整数)和long(长整数) 如果你想将int转为long可以在数据末尾加L

在python3中只有int(整数)
 
如需了解更多,你还可以去看[详情](https://victorfengming.github.io/2019/11/28/python23-long/)

### 6.xrange 和 range 的区别？
如需了解更多,你还可以去看[详情](https://victorfengming.github.io/2019/11/28/python-range-xrange/)



<h3 style="color:inherit;line-height:inherit;font-weight:bold;border-bottom:2px solid rgb(239,112,96);font-size:1.3em;" id="-1">
<span style="font-size:inherit;line-height:inherit;font-weight:normal;background:rgb(239,112,96);color:rgb(255,255,255);">编码规范</span>
<span style="vertical-align:bottom;border-bottom:36px solid rgb(239,235,233);border-right:20px solid transparent;"> </span>
</h3>

### 7.什么是 PEP8?
如需了解更多,你还可以去看[详情](https://victorfengming.github.io/2019/11/28/python-pep8/)

### 8.了解 Python 之禅么？


通过 import this 语句可以获取其具体的内容。告诉人们如何高效整洁的编写代码

Python之禅 by Tim Peters
 
优美胜于丑陋（Python 以编写优美的代码为目标）  
明了胜于晦涩（优美的代码应当是明了的，命名规范，风格相似）  
简洁胜于复杂（优美的代码应当是简洁的，不要有复杂的内部实现）  
复杂胜于凌乱（如果复杂不可避免，那代码间也不能有难懂的关系，要保持接口简洁）  
扁平胜于嵌套（优美的代码应当是扁平的，不能有太多的嵌套）  
间隔胜于紧凑（优美的代码有适当的间隔，不要奢望一行代码解决问题）  
可读性很重要（优美的代码是可读的）  
即便假借特例的实用性之名，也不可违背这些规则（这些规则至高无上）  
 
不要包容所有错误，除非你确定需要这样做（精准地捕获异常，不写 except:pass 风格的代码）  
 
当存在多种可能，不要尝试去猜测
而是尽量找一种，最好是唯一一种明显的解决方案（如果不确定，就用穷举法）  
虽然这并不容易，因为你不是 Python 之父（这里的 Dutch 是指 Guido ）  
 
做也许好过不做，但不假思索就动手还不如不做（动手之前要细思量）  
 
如果你无法向人描述你的方案，那肯定不是一个好方案；反之亦然（方案测评标准）  
 
命名空间是一种绝妙的理念，我们应当多加利用（倡导与号召）  

如需了解更多,你还可以去看[详情](https://victorfengming.github.io/2019/11/28/python-chan/)

### 9.了解 dosctring 么？

DocStrings 文档字符串是一个重要工具，用于解释文档程序，帮助你的程序文档更加简单易懂。

我们可以在函数体的第一行使用一对三个单引号 ''' 或者一对三个双引号 """ 来定义文档字符串。

如需了解更多,你还可以去看[详情](https://victorfengming.github.io/2019/11/28/python-docstring/)



你可以使用 __doc__（注意双下划线）  调用函数中的文档字符串属性
### 10.了解类型注解么？

如需了解更多,你还可以去看[详情](https://victorfengming.github.io/2019/11/28/python-type-annotation/)

### 11.例举你知道 Python 对象的命名规范，例如方法或者类等

类：总是使用首字母大写单词串，如 MyClass(大驼峰命名)。

内部类可以使用额外的前导下划线。 变量：小写，由下划线连接各个单词。方法名类似常量：常量名所有字母大写 等

### 12.Python 中的注释有几种？

总体来说分为两种，单行注释和多行注释。
- 单行注释在行首是 #。
- 多行注释可以使用三个单引号或三个双引号，包括要注释的内容。

### 13.如何优雅的给一个函数加注释？

### 14.如何给变量加注释？

### 15.Python 代码缩进中是否支持 Tab 键和空格混用。

不允许 tab 键和空格键混用，这种现象在使用 sublime 的时候尤为明显。

一般推荐使用 4 个空格替代 tab 键。
### 16.是否可以在一句 import 中导入多个库?
可以是可以，但是不推荐。因为一次导入多个模块可读性不是很好，所以一行导入一个模块会比较好。

同样的尽量少用 from modulename import *，因为判断某个函数或者属性的来源有些困难，不方便调试，可读性也降低了。

### 17.在给 Py 文件命名的时候需要注意什么?
给文件命名的时候不要和标准库库的一些模块重复，比如 abc。 

另外要名字要有意义，不建议数字开头或者中文命名。

与标识符命名规则类似

### 18.例举几个规范 Python 代码风格的工具
pylint 和 flake8








<h3 style="color:inherit;line-height:inherit;font-weight:bold;border-bottom:2px solid rgb(239,112,96);font-size:1.3em;" id="-1">
<span style="font-size:inherit;line-height:inherit;font-weight:normal;background:rgb(239,112,96);color:rgb(255,255,255);">数据类型</span>
<span style="vertical-align:bottom;border-bottom:36px solid rgb(239,235,233);border-right:20px solid transparent;"> </span>
</h3>



## 字符串
### 19.列举 Python 中的基本数据类型？
就那6种么,
如需了解更多,你还可以去看[详情](https://blog.csdn.net/qq_40223983/article/details/95735483)


### 20.如何区别可变数据类型和不可变数据类型

说白了:就看内存地址和数据的值能不能对应上



### 21.将"hello world"转换为首字母大写"Hello World"

字符串操作函数:capitalize()

### 22.如何检测字符串中只含有数字?

isdigit()检测字符串是否由纯数字组成  十进制

isdecimal()纯数值字符串(中文的也好使)

### 23.将字符串"ilovechina"进行反转

"ilovechina"[::-1]

### 24.Python 中的字符串格式化方式你知道哪些？

第一种：%

第二种:format()函数

### 25.有一个字符串开头和末尾都有空格，比如“ adabdw ”,要求写一个函数把这个字符串的前后空格都去掉。

“ adabdw ”.strip()

### 26.获取字符串”123456“最后的两个字符。

”123456“[-2::]

### 27.一个编码为 GBK 的字符串 S，要将其转成 UTF-8 编码的字符串，应如何操作？

a= "S".encode("gbk").decode("utf-8",'ignore')

### 28.s="info:xiaoZhang 33 shandong",用正则切分字符串输出['info', 'xiaoZhang', '33', 'shandong']

```python
import re
 
s = "info：xiaoZhang 33 shandong"
res = re.split(r"：| ", s)
print(res)
```

### 27.怎样将字符串转换为小写？

使用字符串的 lower() 方法。

### 28.单引号、双引号、三引号的区别？

单独使用单引号和双引号没什么区别，但是如果引号里面还需要使用引号的时候，就需要这两个配合使用了，

然后说三引号，同样的三引号也分为三单引号和三双引号，两个都可以声名长的字符串时候使用，如果使用 docstring 就需要使用三双引号。

### 29.a = "你好     中国  ",去除多余空格只留一个空格。

```python
s = "你好     中国  "
print(" ".join(s.split()))
```
## 列表
### 30.已知 AList = [1,2,3,1,2],对 AList 列表元素去重，写出具体过程。

```python
# 用set去重
AList = [1,2,3,1,2]
result_list = list(set(AList))

# 遍历判断
AList = [1,2,3,1,2]
result_list = []
for i in AList:
	if i not in result_list:
		result_list.append(i)
	else:
		continue
print(result_list)

# 使用pandas.unique()
result_list = pandas.unique(AList).tolist()
```

### 31.如何实现 "1,2,3" 变成 ["1","2","3"]
```python
str.split(",")
```
### 32.给定两个 list，A 和 B，找出相同元素和不同元素
```python
different_list = [i for i in A if i not in B]
```
### 33.[[1,2],[3,4],[5,6]]一行代码展开该列表，得出[1,2,3,4,5,6]

使用列表推导式
```python
[ j for i in question_list for j in i]
```
### 34.合并列表[1,5,7,9]和[2,2,6,8]
```python
# solution 1
A + B
# solution 2
A.extend(B)
```
### 35.如何打乱一个列表的元素？
```python
import random
random.shuffle(demo_list)
```
## 字典

### 36.字典操作中 del 和 pop 有什么区别
```python
# pop方法删除指定的键值对，并返回删除的值
demo_dic = {"a": 1, "b": 2, "c": 3}
pop_str = demo_dic.pop("a")
print(demo_dic)
print(pop_str)
# {'b': 2, 'c': 3}
# 返回值 1

# del不会返回相应的值，只是将其删除
del demo_dic["b"]
print(demo_dic)
```
### 37.按照字典的内的年龄排序
```python
d1 = [  
  {'name': 'alice', 'age': 38},
  {'name': 'bob', 'age': 18},
  {'name': 'ctrl', 'age': 28}
]
d1.sort(key=lambda x: x['age'])
```
### 38.请合并下面两个字典 a = {"A":1,"B":2},b = {"C":3,"D":4}
```python
a.update(b)
```
### 39.如何使用生成式的方式生成一个字典，写一段功能代码。
```python
# 生成一个字典
student_dict = {name: "student" for name in ["Robin", "Bob", "James"]}

name_dic = {1: "robin", 2: "bob", 3: "jams"}
result_dict = {k: v.capitalize() for k, v in name_dict.items()}
```

### 40.如何把元组("a","b")和元组(1,2)，变为字典{"a":1,"b":2}
```python
tuple_key = ("a", "b")
tuple_val = (1, 2)
result_dict = dict(zip(tuple_key, tuple_val))
print(result_dict)
```


## 综合
### 41.Python 常用的数据结构的类型及其特性？

字典中的键是不可变类型，可变类型list和dict不能作为字典键

一个对象能不能作为字典的key，就取决于其有没有__hash__方法

### 42.如何将元组("A","B")和元组(1,2),合并成字典{"A":1,"B":2}
```python
result_dict = {v: k for k, v in demo_dict.items()}
```
### 43.Python 里面如何实现 tuple 和 list 的转换？
```python
# tuple()
result_tuple = tuple(demo_list)

# list()
result_list = list(result_tuple)
```
### 44.我们知道对于列表可以使用切片操作进行部分元素的选择，那么如何对生成器类型的对象实现相同的功能呢？
```python
# 可以使用itertools.islice()对迭代器进行切片
import itertools
def fbnq(num):
	a, b = 1, 1
	for _ in range(num):
		a, b = b, a+b
		yield a
if __name__ == '__main__':
	gener = fbnq(20)
	print(gener)
	gener_clip = itertools.islice(gener, 10, 20)
	for i in gener_clip:
		print(i)
```
### 45.请将[i for i in range(3)]改成生成器
```python
(i for i in range(3))    # 方括号改为尖括号即可
```
### 46.a="hello"和 b="你好"编码成 bytes 类型
```python
a.encode()
b.encode()
```
### 47.下面的代码输出结果是什么？

```python
a = (1,2,3,[4,5,6,7],8)
a[2] = 2
```

```python
a = (1, 2, 3, [4, 5, 6, 7], 8)
a[2] = 2   

# TypeError: 'tuple' object does not support item assignment
```

### 48.下面的代码输出的结果是什么?
```python
a = (1,2,3,[4,5,6,7],8)
a[5] = 2
```


```python
a = (1, 2, 3, [4, 5, 6, 7], 8)
a[3][0] = 2 
# (1, 2, 3, [2, 5, 6, 7], 8)
```


元组中有可变数据类型，就可以修改可变数据类型中的值，修改可变数据类型的值并不会使其内存id发生变化。