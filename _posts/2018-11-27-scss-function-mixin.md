---
title: SCSS 的 function 与 mixin 
---

## 用 SCSS 的 function 计算 vw

vw 比 % 要好用。所有宽度用 vw 计算，这样就能动态缩放。

但是计算 vw 有时候会比较麻烦，这时候我们可以引入 function 或者 mixin。

以下以 function 为例：

```scss
@function px($npx) {
    @return $npx/375 * 100vw;
}

div {
    width: px(128);
}
```

假设设计稿的宽度为 375px，我们用上面的 function 计算 vw。

## 用 mixin 写媒体查询

```scss
@mixin phone {
    @media (max-width: 500px) {
        @content;
    }
}

@include phone {
    > ul {
        display: none;
    }
}
```