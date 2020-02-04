---
title: Python 笔记 2
---

## 迭代器（Iterator）

列表、元组、字符串、集合、字典这些容器之所以能被迭代，是因为对它们调用内置函数 iter() 将返回一个迭代器，这个迭代器可被用于迭代操作。

```python
迭代器 = iter(容器)
```

要使用迭代器，只需对迭代器调用内置函数 next()，便可逐一获取其中所有的值。

next() 的使用方法：

```python
值 = next(迭代器)
```

## 可迭代（Iterable）对象

什么是可迭代(的)？

* 从表面来看，所有可用于 for 循环的对象是可迭代的，如列表、元组、字符串、集合、字典等容器

* 从深层来看，定义了 `__iter__()` 方法的类对象就是可迭代的。当这个类对象被 iter() 函数使用时，将返回一个迭代器对象。如果对象具有 `__iter__()` 方法，则可以说它支持迭代协议。

判断一个已有的对象是否是可迭代的的 2 种方法：

1，通过内置函数 dir() 获取这个对象所有方法，检查是否有 `__iter__`

```python
>>> ‘__iter__’ in dir(list)
True
>>> ‘__iter__’ in dir(int)
False
```

2，使用内置函数 isinstance() 判断其是否为 Iterable 的对象

```python
>>> from collections.abc import Iterable
>>> isinstance([1, 2, 3], Iterable)
True
```

## 自定义迭代器

我们可以自己来定义迭代器类，只要在类中定义 `__next__()` 和 `__iter__()` 方法即可。如果对象具有 `__iter__()` 和 `__next__()` 方法，则可以说它支持迭代器协议。

```python
class MyIterator:
    def __next__(self):
        代码块

    def __iter__(self):
        return self
```

## 生成器（Generator）

```python
def power_of_two():
	for exponent in range(11):	# range(11) 表示左开右闭区间 [0, 11)，不包含 11
		yield 2 ** exponent	
```

## 生成器表达式（Generator Expression）

```python
生成器 = (针对项的操作 for 项 in 可迭代对象)
```

例子：

```python
letters = (item for item in ‘abc’)
letters2 = (i.upper() * 2 for i in ['3','2','1'])
```