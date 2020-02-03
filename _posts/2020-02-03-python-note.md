---
title: Python 笔记
---

## 错误处理

在 Python 中大多数情况下，错误是以抛出异常的方式报告出来，可以针对潜在的异常来编写处理代码。

可使用 try-except 语句捕获异常

异常的捕获使用 try-except 语句：

```python
try:
    代码块1
except 异常X as e:
    代码块2
```

捕获多个异常：

```python
try:
    代码块1
except (异常X, 异常Y, 异常Z) as e:
    代码块2
```

```python
try:
    代码块1
except 异常X as e:
    代码块2
except 异常Y as e:
    代码块3
except 异常Z as e:
    代码块4
```

finally 语句紧接着 try-except 的流程执行：

```python
try:
    代码块1
except 异常X as e:
    代码块2
finally:
    代码块3
```

使用 raise 语句可主动抛出异常：

```python
raise ValueError()
```

## Pass

```python
def sample(n_samples):
    pass
```
pass 是占位符，表示什么都不做或什么都没有。它用来占据一个位置，因为如果定义一个空函数程序会报错。

## Package

Python 中可以用文件树这样的树形结构来组织模块，这种组织形式下的模块集合称为包（Package）。

包的结构可以是这样：

```
包/
├── __init__.py
├── 模块1.py
├── 模块2.py
├── 子包1/
|   ├── __init__.py
|   ├── 模块3.py
|   └── 模块4.py
└── 子包2/
    ├── __init__.py
    ├── 模块5.py
    └── 孙子包1/
        ├── __init__.py
        └── 模块6.py
```

只有当目录中存在 `__init__.py` 时，Python 才会把这个目录当作包。

导入包中模块的方法是：

```
import 包.子包.模块
```

导入模块使用 import 语句：

```
import 模块名
```

导入包下的模块：

```
import 包名.模块名
```

模块导入后，可以使用该模块中所定义的名字（变量、函数类）。方式如下：

```
模块名.变量
模块名.函数
模块名.类
```
