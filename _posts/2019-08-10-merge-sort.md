---
title: 归并排序
---

```javascript
function merge(left, right) {
  console.log("merge begin", left, right);
  var result = [];
  while (left.length > 0 && right.length > 0) {
    if (left[0] < right[0]) {
      result.push(left.shift());
    } else {
      result.push(right.shift());
    }
  }
  console.log("merge end", result.concat(left).concat(right));
  return result.concat(left).concat(right);
}

function mergeSort(arr) {
  if (arr.length === 1) {
    return arr;
  }
  var mid = Math.floor(arr.length / 2);
  var left_arr = arr.slice(0, mid);
  var right_arr = arr.slice(mid);
  return merge(mergeSort(left_arr), mergeSort(right_arr));
}

var arr = [23, 6, 55, 22, 4];
console.log(mergeSort(arr));
```