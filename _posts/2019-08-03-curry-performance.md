---
title: 从柯里化中学到的性能优化技巧
---

## 参数复用

如果是相同的参数，在计算之后不需要再次重新传入参数。

```javascript
function add(a){
	return function(b){
		return function(c){
			return a + b + c;
		}
	}
}

console.log(add(1)(2)(3)); // 6

var add1 = add(1);
var add2 = add1(2);
console.log(add2(3)); // 6
```

## 提前返回

多次调用多次内部判断，可以直接把第一次判断的结果返回外部接收。

```javascript
var addEvent = function(){
	if(window.addEventListener){
		return function(el,type,fn,capture){
			// ...
		}
	}
	if(window.attachEvent){
		return function(el,type,fn,capture){
			// ...
		}
	}
}

var addEvent_new = addEvent();
addEvent_new(div,click,callback,false);
addEvent_new(span,click,callback,false);
```

## 延迟执行

避免重复地去执行程序，等真正需要结果的时候再执行。

```javascript
var curryScore = function(fn){
	var _allScore=[];
	return function(){
		if(arguments.length===0){
			 fn.apply(null,_allScore);
		}
		_allScore=_allScore.concat([].slice.call(arguments))
	}
}
var allScore=0;
var addScore = curryScore(function(){
	for (var i = 0; i < arguments.length; i++) {
		allScore += arguments[i]
  }
})

addScore(1)
addScore(5)
console.log(allScore) // 0
addScore()
console.log(allScore) // 6
```
