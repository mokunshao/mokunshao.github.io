---
title: transform
---

transform 只改变元素的外观而不改变元素的实际大小。

默认值为 transform: none;

## translate

translate 用于移动元素。

transform: translate(X轴的移动距离,Y轴的移动距离);

transform: translateX(移动距离);

transform: translateY(移动距离);

transform: translateZ(移动距离)

transform: translate3d(X轴的移动距离,Y轴的移动距离,Z轴的移动距离)

```css
transform: translate(20px, -10%);
```

## rotate

rotate 用于旋转元素。

transform: rotate(旋转角度);

transform: rotateX(X轴的旋转角度)

transform: rotateY(Y轴的旋转角度)

transform: rotateZ(Z轴的旋转角度)

transform: rotate3d(X坐标,Y坐标,Z坐标,旋转角度)

```css
transform: rotate(45deg);
```

## scale

scale 用于放大元素。

transform: scaleX(X轴的放大倍数);

transform: scaleY(Y轴的放大倍数);

transform: scale(X轴的放大倍数,Y轴的放大倍数);

transform: scaleZ(Z轴的放大倍数)

transform: scale3d(X轴的放大倍数,Y轴的放大倍数,Z轴的放大倍数)

```css
transform: scale(0.8, 0.8);
```

## skew

skew 用于使元素倾斜。

transform: skewX(X轴的倾斜度);

transform: skewY(Y轴的倾斜度);

transform: skew(X轴的倾斜度, Y轴的倾斜度);

```css
transform: skew(10deg, -20deg);
```

## transform-origin

transform-origin 用于确定基准点。

transform-origin: X轴的基准位置 Y轴的基准位置;

```css
transform-origin: 20px 70%;
```

## matrix

matrix 可以使元素进行旋转、缩放、移动或倾斜。

transform: matrix(n,n,n,n,n,n)

transform: matrix3d(n,n,n,n,n,n,n,n,n,n,n,n,n,n,n,n)

```css
transform: matrix(0.707,0.707,-0.707,0.707,0,0);
```