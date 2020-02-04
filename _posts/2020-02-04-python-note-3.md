---
title: Python 笔记 3
---

## 列表生成式

```python
[对项的操作 for 项 in 可迭代对象]
```

```python
[char.upper() for char in ['a', 'b', 'c', 'd', 'e']]
```

## 列表生成式中使用 if

```python
[对项的操作 for 项 in 可迭代对象 if 对项的判断]
```

```python
[2 ** i for i in range(1, 11) if i % 2 == 1 ]
```

## 列表生成式中嵌套 for

```python
[对项1和(或)项2的操作 for 项1 in 可迭代对象1 for 项2 in 可迭代对象2]
```

```python
nums = [1, 2, 3]
chars = ['a', 'b', 'c']
[c * n for n in nums for c in chars]
```

```python
strings = ['aa', 'bb', 'cc']
[char for string in strings for char in string]
```

## 字典生成式

```python
{键: 值 for 项 in 可迭代对象}
```

```python
{char: char.upper() for char in 'abcde'}
```

## 集合生成式

```python
{对项的操作 for 项 in 可迭代对象}
```

```python
{char.lower() for char in 'ABCDABCD'}
```
