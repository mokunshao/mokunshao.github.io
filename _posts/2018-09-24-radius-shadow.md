---
title: 矩形的圆角与阴影
---

## border-radius

矩形的圆角通过 border-radius 属性设置。

值为 0 时移除所有圆角。

值可以为像素值，也可以为百分比。

你可以单独设置一个部分的圆角：

- border-top-left-radius

- border-top-right-radius

- border-bottom-right-radius

- border-bottom-left-radius

border-radius 可以接受多个值。

## box-shadow

矩形的阴影通过 box-shadow 属性设置。

box-shadow 至少要有两个值，第一个参数为水平方向的偏移值，第二个参数为垂直方向的偏移值。

接下来的为可选参数：

第三个值为 blur，指模糊距离。

第四个值为 spread，指阴影的尺寸。

color 参数可以填颜色的英文代码、HEX 格式或者 RGB 格式。

inset 参数可以将阴影变成内部阴影。

### 双重阴影

box-shadow 可以实现多重阴影，只需要用逗号隔开即可。

```css
div{
    box-shadow: 0 0 0 1px #1a1b1c, 0 0 0 2px #1f2020, 0 3px 0 2px black;    
}
```