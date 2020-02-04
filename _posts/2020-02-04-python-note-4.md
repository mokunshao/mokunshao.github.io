---
title: Python 笔记 4
---

## 关键字参数

在调用函数时以 `参数名=值` 指明要传递的参数，这种以关键字的形式来使用的参数叫做关键字参数。

```python
def example(first, second, third):
    pass

example(second=12, third=90, first=55)
```

如果参数列表中某个参数使用 `**参数名` 形式，那么这个参数可以接受一切关键字参数。如下：

```python
def echo(string, **keywords):
    print(keywords)

echo('hello', today='2019-09-04', content='function', section=3.6)
```

## 任意参数列表

参数列表中使用 `*参数名`，就可以接受任意数量的非关键字参数，也就是可变参数。

```python
def multiply(*nums):
    print(nums)

multiply(1,2,3,4,5)
```

## 多返回值

```python
def example():
    return 1, 2, 3

data = example()
first, second, third = example()
```