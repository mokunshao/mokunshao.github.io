---
title: 简单算法
---

### 是否包含

```
效果：
includes(['javascript','java'])  // true
includes(['floor','for'])  // true
```

```javascript
function includes(arr){
  return arr[1].toLowerCase().split('').every(item=>arr[0].includes(item));
}

console.log(includes(['floor','for']));  // true
```

### 分割数组

```javascript
function sliceArray(arr, size) {
  let resArr = [];
  for (let i = 0; i < arr.length; i += size) {
    resArr.push(arr.slice(i, i + size));
  }
  return resArr;
}

console.log(sliceArray([0, 1, 2, 3, 4, 5, 6, 7], 3)); // [[0,1,2],[3,4,5],[6,7]]
```

```javascript
function sliceArray(arr, size) {
  if (arr.length <= size) {
    return [arr];
  } else {
    return [arr.slice(0, size), ...sliceArray(arr.slice(size), size)];
  }
}

console.log(sliceArray([0, 1, 2, 3, 4, 5, 6, 7], 3));// [[0,1,2],[3,4,5],[6,7]]
```

### 洗牌

```javascript
function shuffle(arr) {
  return arr.sort(() => {
    return Math.random() - 0.5;
  });
}

console.log(shuffle([0, 1, 2, 3, 4, 5, 6, 7]));
```

```javascript
function shuffle(arr) {
  for (let i = arr.length - 1; i > 0; i--) {
    let randomIndex = Math.floor(Math.random() * (i + 1));
    [arr[randomIndex], arr[i]] = [arr[i], arr[randomIndex]];
  }
  return arr;
}

console.log(shuffle([0, 1, 2, 3, 4, 5, 6, 7]));
```
