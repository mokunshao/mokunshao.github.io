---
title: TypeScript 泛型
---

## 定义

泛型（Generics）是指在定义函数、接口或类的时候，不预先指定具体的类型，而在使用的时候再指定类型的一种特性。

泛型就是用一个东西表示广泛的类型。

```typescript
function returnIt<T>(arg: T): T {
  return arg;
}

let s = returnIt<string>("hi");
```

## 泛型约束

就是给泛型添加一些约束。

添加约束之前，这是错的：

```typescript
function returnIt<T>(arg: T): T {
  console.log(arg.length); // error
  return arg;
}
```

添加约束之后：

```typescript
interface HasLength {
  length: number;
}

function returnIt<T extends HasLength>(arg: T): T {
  console.log(arg.length); // no error
  return arg;
}

returnIt(['12',34])
returnIt<any[]>(['12',34])
returnIt<number[]>([12,34])
returnIt<string[]>(['12','34'])
```
