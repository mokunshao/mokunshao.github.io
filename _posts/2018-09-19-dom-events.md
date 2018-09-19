---
title: DOM Events 笔记
---

## onclick

```html
<button id='X' onclick = "print">A</button> // 这是错的
<button id='Y' onclick = "print()">B</button> // ✅可以运行
<button id='Z' onclick = "print.call()">C</button> // ✅可以运行

<!--  onclick = "要执行的代码" -->
<!-- 一旦用户点击，浏览器就 eval("要执行的代码") eval("print") -->
```

```javascript
X.onclick = print // ✅可以运行 类型为函数对象
Y.onclick = print() // undefined 这是错的
Z.onclick = print.call() // undefined 这是错的

// 一旦用户点击，那么浏览器就运行
// X.onclick.call(x,{ }) 
```

## EventListener

对于同一个 id 的元素，onclick 只能有一个。

出现两个的话后者会覆盖前者，这是 onclick 的缺陷。

而 EventListener 是一个队列。

```javascript
xxx.addEventListener('click', function(){
    console.log(1)
})

xxx.addEventListener('click', function(){
    console.log(2)
})

// xxx 拥有一个队列 eventListeners
// 点击后输出1后输出2
```

```javascript
function f1(){
    console.log(1)
}

function f2(){
    console.log(2)
}

function f3(){
    console.log(3)
}

xxx.addEventListener('click', f1)
xxx.addEventListener('click', f2)
xxx.removeEventListener('click', f1)
xxx.addEventListener('click', f3)
xxx.removeEventListener('click', f3)

// 点击后输出2
```

## jQuery 的 one() 方法 

与 on() 不同，one() 只执行一次

它的实现方式如下：

```javascript
function f1(){
    console.log(1)
    xxx.removeEventListener('click', f1)    
}

xxx.addEventListener('click', f1)
```

## DOM 事件流　

![](https://raw.githubusercontent.com/mokunshao/images/master/Event-Capturing-and-Bubbling.png)

```html
<div class="grandpa">爷爷
    <div class="dad">爸爸
        <div class="son">儿子
        </div>
    </div>
</div>
```

```javascript
grandpa.addEventListener('click', function fn1(){
    console.log('爷爷')
})
dad.addEventListener('click', function fn1(){
    console.log('爸爸')
})
son.addEventListener('click', function fn1(){
    console.log('儿子')
})

// 1. 当点击儿子时，我是否点击了爸爸和爷爷？
// 是的

// 2. 当我点击儿子时，三个函数是否调用？
// 是的

// 3. 请问 fn1 fn2 fn3 的执行顺序？
// addEventListener 可以添加第三个参数
// 如果不填或者填 false：儿子爸爸爷爷
// 如果填写 true：爷爷爸爸儿子
```

```javascript
grandpa.addEventListener('click', function fn1(){
    console.log('爷爷')
})
dad.addEventListener('click', function fn1(){
    console.log('爸爸')
})
son.addEventListener('click', function fn1(){
    console.log('儿子1')
})
son.addEventListener('click', function fn1(){
    console.log('儿子2')
})

// 3. 请问 儿子1 和 儿子2 的执行顺序？
// 对于同一个元素，谁在前谁先执行
```

```javascript
grandpa.addEventListener('click', function fn1(){
    console.log('爷爷')
},true)
dad.addEventListener('click', function fn1(){
    console.log('爸爸')
})
son.addEventListener('click', function fn1(){
    console.log('儿子')
})

// 点击后的执行顺序？
// 爷爷儿子爸爸
```

```javascript
son.addEventListener('click', function fn1(){
    console.log('儿子捕获')
},true)
son.addEventListener('click', function fn1(){
    console.log('儿子冒泡')
},false)

// 特例：如果同一元素同时有捕获和冒泡，执行顺序为写的顺序，谁先写谁先执行
// 顺序：儿子捕获，儿子冒泡
```

```javascript
son.addEventListener('click', function fn1(){
    console.log('儿子冒泡')
},false)
son.addEventListener('click', function fn1(){
    console.log('儿子捕获')
},true)

// 特例：如果同一元素同时有捕获和冒泡，执行顺序为写的顺序，谁先写谁先执行
// 顺序：儿子冒泡，儿子捕获
```

DOM 事件流的三个阶段：

1. 捕获阶段

2. 目标阶段

3. 冒泡阶段