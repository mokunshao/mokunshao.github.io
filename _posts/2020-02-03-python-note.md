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
