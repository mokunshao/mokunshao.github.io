---
title: Python 笔记 6
---

## lambda 表达式

在 Python 中，可以通过 lambda 表达式来便捷地定义一个功能简单的函数，这个函数只有实现没有名字，所以叫作匿名函数。

```python
lambda 参数1, 参数2, 参数N: 函数实现
```

## 拆包

```python
a, *b = (1, 2, 3, 4)
# a 为 1，b 为 [2, 3, 4]
```

```python
*a, b = (1, 2, 3, 4)
# a 为 1，b 为 [2, 3, 4]
```

## 切片

```python
chars = [‘a’, ‘b’, ‘c’, ‘d’, ‘e’]
chars[1:3] # [‘b’, ‘c’]
chars[:3] # [‘a’, ‘b’, ‘c’]
chars[3:] # [‘d’, ‘e’]
chars[:] # [‘a’, ‘b’, ‘c’, ‘d’, ‘e’]
chars[1:-2] # [‘b’, ‘c’]
chars[-3:-1] # [‘c’, ‘d’]
```

## if 三元表达式

```python
结果1 if 条件 else 结果2
```

## for else 语句

```python
for i in range(5):
    print(i)
else:
    print('所有项被迭代使用')
```

如果循环被 break 就不会执行 else 里的语句。

## while else 语句

```python
i = 0
while i < 5:
    print(i)
    i += 1
else:
    print('这是 else 语句')
```

如果循环被 break 就不会执行 else 里的语句。

## try except else 语句

```python
try:
    pass
except:
    print('有异常发生，不执行 else 语句')
else:
    print('没有异常发生，执行 else 语句')
```

如果 try 下有异常抛出，则不执行 else 语句。如果没有异常抛出，则执行 else 语句。

## @property

```python
class A:
    @property
    def apple(self):
        return 'apple'

a = A()
a.apple # 'apple'
```

被 @property 装饰的方法，可以像属性一样被使用。但是有一个限制，这个属性是只读的，不能被修改。如果修改将会报错。

让这个 apple 属性变得可修改：

```python
class A:
    def __init__(self, name):
        self._apple = name

    @property
    def apple(self):
        return self._apple

    @apple.setter
    def apple(self, value):
        self._apple = value
```

## 自定义异常

自定义异常的方式很简单，只需要定义一个类，这个类继承自 Exception 类或其子类即可。如：

```python
class FileParseException(Exception):
    pass
```

## 类型标注

可以为函数的加上参数类型标注，以及返回值类型标注。

```python
def say_hello2(name: str) -> str:
    word = 'hello, ' + name
    return word
```