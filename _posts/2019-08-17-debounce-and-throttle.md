---
title: 防抖与节流
---

```javascript
function debounce(fn, delay) {
  let timerId = null;
  return function() {
    if (timerId) {
      window.clearTimeout(timerId);
    }
    timerId = setTimeout(() => {
      fn.apply(this, arguments);
    }, delay);
  };
}
```

```javascript
function throttle(fn, delay) {
  let canUse = true;
  return function() {
    if (canUse) {
      fn.apply(this, arguments);
      canUse = false;
      setTimeout(() => (canUse = true), delay);
    }
  }
}
```