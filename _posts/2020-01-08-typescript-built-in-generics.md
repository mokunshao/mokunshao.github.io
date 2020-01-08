---
title: 'TypeScript: 内置泛型'
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

JavaScript 中的 `const` 很狡猾，因为它虽然意味着你不能将任何其他值重新分配给此常量，但是允许更改对象的属性。`Readonly` 内置类型可以解决这个问题。

```typescript
type Point = {
  x: number,
  y: number
};

const p: Readonly<Point> = {
  x: 4,
  y: 2
};

p.x = 5; // ❌ 编译错误!
```

## ReadonlyArray

`ReadonlyArray` 允许我们在使用改变原始数组的数组函数时抛出错误。

```typescript
const values: ReadonlyArray<number> = [1, 2, 3, 4, 5];

values.push(6); // ❌ 编译错误！这会使数组发生变化
values.filter(x => x > 4); // ✅ 编译通过！filter 返回新数组
```

如果你想要让一个数组不可变（immutable），这样做会很方便。

## ReturnType

此内置类型为你提供任何函数的返回类型。

```typescript
type Point = {
  x: number,
  y: number
}

function generateSquare(bottomLeft: Point, topRight: Point) {
  return {
    bottomLeft,
    bottomRight: {
      x: topRight.x,
      y: bottomLeft.y,
    },
    topLeft: {
      x: bottomLeft.x,
      y: topRight.y
    },
    topRight
  }
}

type Square = ReturnType<typeof generateSquare>; 
// 现在我可以在代码的任何地方使用此返回类型。

function areaOfSquare(square: Square): number {
  //做一些事情...
  return result;
}
```

您还可以访问类内的函数：

```typescript
class Square {
  generate(bottomLeft, topRight) {
    return {
      bottomLeft,
      bottomRight: {
        x: topRight.x,
        y: bottomLeft.y,
      },
      topLeft: {
        x: bottomLeft.x,
        y: topRight.y
      },
      topRight
    }
  }
}

type TSquare = ReturnType<Square['generate']>;
declare let result: TSquare;
```

## Partial

`Partial<T>` 从一个类型中获取所有属性，并使它们成为可选的。它有什么好处？试想现在有一组默认选项，当你想覆盖其中的部分属性时就很有用了。`Partial<T>` 可帮你针对该情况自动完成和类型检查：

```typescript
const defaultOptions = {
  directory: '.',
  incremental: true, 
  filePattern: '**/*',
}

function start(options: Partial<typeof defaultOptions>) {
  const allOptions = Object.assign({}, defaultOptions, options);
  console.log(allOptions); 
}

start({
  incremental: false, // ✅ 类型检查通过
});

start({
  flatten: true // ❌ 报错，此属性与我们的选项无关
});
```

## Required
## NonNullable
## Pick
## Record
## Extract
## Exclude
## Omit
## Bottom line