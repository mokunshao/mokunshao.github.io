---
title: TypeScript: 内置泛型
---

> 本文翻译自 stefan baumgartner 的 《TypeScript: Built-in generic types》，原文：[TypeScript: Built-in generic types](https://fettblog.eu/typescript-built-in-generics/)

TypeScript 附带大量内置泛型类型，可以简化你的开发工作流程。下面是所有内置泛型类型的列表，并附有示例。

注意：此列表可能（几乎肯定）不完整。如果你遗漏了什么，并且想要添加它，请通过 [Twitter](https://twitter.com/ddprrt) 联系我。

本文提到了：

* Readonly
* ReadonlyArray
* ReturnType
* Partial
* Required
* NonNullable
* Pick
* Record
* Extract
* Exclude
* Omit
* Bottom line

## Readonly

JavaScript 中的 `const` 很棘手，因为它虽然意味着你不能将任何其他值重新分配给此变量，但是允许更改对象的属性。`Readonly` 内置类型有助于：

```javascript
type Point = {
  x: number,
  y: number
};

const p: Readonly<Point> = {
  x: 4,
  y: 2
};

p.x = 5; // ⚡️ 编译错误!
```

## ReadonlyArray
## ReturnType
## Partial
## Required
## NonNullable
## Pick
## Record
## Extract
## Exclude
## Omit
## Bottom line