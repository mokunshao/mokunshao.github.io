---
title: 两种数组去重的方案
---

著名面试题：

如何实现数组去重？

假设有数组 array = [1,5,2,3,4,2,3,1,3,4]

你要写一个函数 unique，使得

unique(array) 的值为 [1,5,2,3,4]

也就是把重复的值都去掉，只保留不重复的值。

要求：

不要做多重循环，只能遍历一次

请给出两种方案，一种能在 ES 5 环境中运行，一种能在 ES 6 环境中运行（提示 ES 6 环境多了一个 Set 对象）

### ES5

```javascript
function unique(array){
    var tempArr = []
    var obj = {}
    for(var i=0; i<array.length; i++){
        if(obj[array[i]] === undefined){
            tempArr.push(array[i])
            obj[array[i]] = 1
        }
    }
    return tempArr
}
```

### ES6

利用 set 对象去重：

```javascript
function unique(array) {
    return [...new Set(array)]
}
```

```javascript
function unique(array) {
    return Array.from(new Set(array))
}
```