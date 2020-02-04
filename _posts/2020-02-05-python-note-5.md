---
title: Python 笔记 5
---

## 类属性和类方法

类属性和类方法可以直接使用，无需实例一个对象：

```python
类.属性
类.方法()
```

定义类属性：

```python
class 类：
    属性1 = X
```

定义类方法：

```python
class 类:
	@classmethod
    def 类方法(cls):
        pass
```

类属性和类方法同时使用：

```python
import random

class Char:
    letters = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ'
    digits = '0123456789'
	
    @classmethod
    def random_letter(cls):
        return random.choice(cls.letters)
	
    @classmethod
    def random_digits(cls):
        return random.choice(cls.digits)

print(Char.letters)
print(Char.random_digits())
```

## 静态方法

```python
class 类:
    @staticmethod
    def 静态方法():
        pass
```

## 私有属性、方法

将属性或方法的名称用 `__`（两个下划线）开头即可把属性和方法变成私有。

```python
import random

class Char:
    __letters = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ'
    __digits = '0123456789'
	
    @classmethod
    def random_letter(cls):
        return random.choice(cls.__letters)
	
    @classmethod
    def random_digits(cls):
        return random.choice(cls.__digits)
```

## 继承

```python
class 父类:
    父类的实现
    
class 子类(父类)：
	子类的实现
```

```python
class A:
    def __init__(self):
        self.apple = 'apple'
    
    def have(self):
        print('I hava an', self.apple)


class B(A):
	def __init__(self):
		super().__init__()
		self.banana = 'banana'
	
	def have(self):
		print('I hava an', self.banana)
```

## 继承链

```python
class A:
	def have(self):
		print('I hava an apple')

class B(A):
	pass

class C(B):
	pass
```

在这里 A 是继承链的顶端，B 和 C 都是它的子类。

其实 A 也有继承，它继承自 `object`。任何类的根源都是 `object` 类。如果一个类没有指定所继承的类，那么它默认继承 `object`。

A 中也可以显式指明其继承于 `object`：

```python
class A(object):
	def have(self):
		print('I hava an apple')
```

如果想要判断一个类是否是另一个类的子类，可以使用内置函数 `issubclass()`。

## 多继承

```python
class A:
    def get_apple(self):
        return 'apple'

class B:
    def get_banana(self):
        return 'banana'

class C(A, B):
    pass
```

