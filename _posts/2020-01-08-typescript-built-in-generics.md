---
title: 'TypeScript: 内置泛型'
---

> 本文翻译自 stefan baumgartner 的 《TypeScript: Built-in generic types》，原文：[TypeScript: Built-in generic types](https://fettblog.eu/typescript-built-in-generics/)

TypeScript 附带大量内置泛型，可以简化你的开发工作流程。下面是所有内置泛型的列表，并附有示例。

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

`Required<T>` 与 `Partial<T>` 相反，当 `Partial<T>` 让每个属性变得可选, `Required<T>` 让每个属性变成必须。

```typescript
type Container = {
  width: number,
  height: number, 
  children?: Container[]
}

function getChildrenArea(parent: Required<Container>) {
  let sum = 0;
  for (let child of parent.children) {
    sum = sum + (child.width * child.height)
  }
  return sum;
}

const mainContainer: Container = {
  width: 200,
  height: 100
}

getChildrenArea(mainContainer); // ❌ 报错，缺少 children 属性
```

## NonNullable

`NonNullable<T>` 帮你确保不会将 `null` 或 `undefined` 传递给函数。它会补充 `strictNullChecks` 编译器 flag，所以确保你是否要启用它。

```typescript
function print<T>(x: NonNullable<T>) {
  console.log(x.toString());
}

print('Hello');
print(2);
print(null); // ❌ 报错
print(undefined); // ❌ 报错
```

## Pick

使用 `Pick<T, K extends keyof T>`，你只需使用选定的属性列表，就可以从现有对象创建新类型。Lodash 的同名 pick 函数就是其用法的一个很好的例子：

```typescript
/**
 * The pick function is generic as well. It has two generic types:
 * - T ... the type of the object we want to pick props from
 * - K ... a subset of all keys in T
 *
 * Our method signature takes an object of type T, the other parameters
 * are collected in an array of type K.
 *
 * The return type is a subset of keys of T.
 */
declare function pick<T, K extends keyof T>(obj: T, ...propsToPick: K[]): Pick<T, K>;

const point3D = {
  x: 2,
  y: 0,
  z: 4
}

const point2D = pick(point3D, 'x', 'y'); // 返回类型 { x: number, y: number }
```

当与其他泛型类型（例如 `Exclude`）一起使用时，此类型特别有用。

## Record

`Record<K, T>` 很有趣。有了它，你可以说每个键 K 都应该是 T 类型。有了它，你可以做以下事情：

```typescript
type Person = Record<'firstName' | 'lastName', string>
```

与 `{firstName：string，lastName：string}` 相同。或者类似于:

```typescript
type MetaInfo = {
  title: string,
  url: string
}

type Episodes = Record<string, MetaInfo>
```

它允许对象具有任何可能的 key，但 value 类型为 MetaInfo。这与 `{[k：string]：MetaInfo}` 非常相似。

到现在为止还好。但是，如果我们可以使用其他方法获得类似的结果，为什么还要使用 Record 类型呢？Record 在处理其他泛型类型时很有帮助。让我们看一下该示例：我们可以创建一个函数，将对象所有 key 转换为字符串表示形式：

```typescript
// 它将所有值转换为字符串。
declare function allToString<T>(obj: T): Record<keyof T, string>;

const person = {
  firstName: 'Stefan',
  lastName: 'Baumgartner',
  age: Number.MAX_VALUE
}

// 现在 strPerson 中的所有属性都是字符串
const strPerson = allToString(person);
```

## Extract

`Extract<T, K>` 从 T 中提取可赋值给 K 的所有类型。假设您有两种不同类型的形状。圆形和矩形。它们看起来就像这样：

```typescript
const rect = {
  width: 200,
  height: 100,
  area() {
    return this.width * this.height;
  },
  perimeter() {
    return this.width * 2 + this.height * 2;
  }
}

const circle = {
  r: 50,
  area() {
    return this.r * this.r * Math.PI;
  },
  perimeter() {
    return 2 * this.r * Math.PI;
  }
}
```

它们的类型是：

```typescript
type Rect = typeof rect;
type Circle = typeof circle;
```

它们有一个共同点：它们都有相同的面积和周长计算方法。这些对象可能会随着时间的推移而更改。我们仍然希望确保我们只访问在这两个方法中都可用的方法。使用 Extract，我们可以获得这些函数的 key：

```typescript
// 提取: 'area' | 'perimeter'
type ShapeFunctionProps = Extract<keyof Rect, keyof Circle>
```

要再次创建可以访问所有这些函数的类型，我们可以使用前面的 Record 类型：

```typescript
type ShapeFunctions = Record<ShapeFunctionProps, () => number>
```

现在，我们在函数中有了可能适用于所有这些对象的额外类型安全：

```typescript
declare function extensiveMath<T extends ShapeFunctions>(obj: T)

extensiveMath(rect); // ✅ 通过编译
extensiveMath(circle); // ✅ 通过编译
```

## Exclude

`Exclude<T, K>` 从 T 中排除可赋值给 K 的所有类型。它类似于 `Extract` 的反义词。让我们以前面的例子为例：

```typescript
type Rect = typeof rect;
type Circle = typeof circle;

// 只有 'width' | 'height';
type RectOnlyProperties = Exclude<keyof Rect, keyof Circle>;

// An object of type { width: number, height: number }
type RectOnly = Pick<Rect, RectOnlyProperties>;

declare function area<T extends RectOnly>(obj: T)

area({
  width: 100,
  height: 100
})  // ✅ 编译通过;
```

## Omit

从 3.5 版本开始，TypeScript 包括 `Omit<T，K>` 类型。`Omit<T，K>` 是 `Pick<T，Exclude<key of T，K>>` 的快捷方式，但由于使用频率很高，团队决定添加它：

```typescript
type Person = {
    name: string;
    age: number;
    location: string;
};

type Cosmopolitan = Omit<Person, 'location'>;

// 相等于
type Cosmopolitan = {
    name: string;
    age: number;
};
```
## 最后

这些是可能对不同情况有用的内置泛型。我认为如果你想要在不过受多干扰的情况下强化你的库或应用程序，所有这些泛型类型的组合是非常有帮助的。特别是当你为接受不同参数类型的方法生成类型定义时（就像 JavaScript 中经常发生的那样），它们可能比自己定义每个可能的类型结果更有用。

再说一次，我肯定我还有很多不知道的。所以如果您有任何想要在这里进行转换的内置泛型，请让我[知道](https://twitter.com/ddprrt)。

更新：我的伙伴 Martin Hochel 有几个建立在这些类型之上的映射类型。它们相当不错，所以快来[看看](https://github.com/Hotell/rex-tils#2-compile-time-typescript-type-helpers)吧。