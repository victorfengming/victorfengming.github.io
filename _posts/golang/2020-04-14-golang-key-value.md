---
title: "盘点key value在各个编程语言中的类型"
subtitle: "站在巨人的肩膀上，吸收了同伴的特点"
tags: Golang base
---


## 起步

## 正文
### python
key value 叫做字典

dict类型
声明

字典操作
以键值对方式存在的无序数据的组合就是字典
```python
方式1：
    变量 = {}

方式2：
    变量 = dict()
```

详细信息可以参考[这里](http://victorfengming.gitee.io/course/python_book/%E5%86%85%E7%BD%AE%E5%87%BD%E6%95%B0%E5%8F%8A%E6%93%8D%E4%BD%9C/%E5%AD%97%E5%85%B8.html)


### Java
在Java里面,具有key-value类型的数据为
hashmap类型

HashMap<K,V>：存储数据采用的哈希表结构，元素的存取顺序不能保证一致。由于要保证键的唯一、不重复，需要重写键的hashCode()方法、equals()方法。

详细信息可以参考[这里](https://victorfengming.gitee.io/2019/10/21/note08/)


### php

Array 数组 :
PHP 中的数组实际上是一个有序映射。映射是一种把 values 关联到 keys 的类型。此类型在很多方面做了优化，因此可以把它当成真正的数组，或列表（向量），散列表（是映射的一种实现），字典，集合，栈，队列以及更多可能性。由于数组元素的值也可以是另一个数组，树形结构和多维数组也是允许的。

```php
<?php
$array = array(
    "foo" => "bar",
    "bar" => "foo",
);

// 自 PHP 5.4 起
$array = [
    "foo" => "bar",
    "bar" => "foo",
];
?>
```



详细信息可以参考[这里](https://victorfengming.gitee.io/2019/10/13/array/#php%E6%95%B0%E7%BB%84)

### golang
map是Go中的内置类型，它将一个值与一个键关联起来。可以使用相应的键检索值。

Map 是一种无序的键值对的集合

Map 最重要的一点是通过 key 来快速检索数据，key 类似于索引，指向数据的值


Map 是一种集合，所以我们可以像迭代数组和切片那样迭代它。不过，Map 是无序的，我们无法决定它的返回顺序，这是因为 Map 是使用 hash 表来实现的，也是引用类型

详细信息可以参考[这里](https://victorfengming.gitee.io/2020/04/13/golang-map/)