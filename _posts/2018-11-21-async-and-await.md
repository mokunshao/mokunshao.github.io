---
title: async 与 await
---

async/await 是写异步代码的新方式，以前的方法有回调函数和 Promise。

async/await 是基于 Promise 实现的，它不能用于普通的回调函数。

async/await 与 Promise 一样，是非阻塞的。

async/await 使得异步代码看起来像同步代码，这正是它的魔力所在。

## async

一个 async 函数是定义会返回 promise 的函数的简便写法。

```javascript
function f() {
    return Promise.resolve('TEST');
}

// asyncF is equivalent to f!
async function asyncF() {
    return 'TEST';
}
```

```javascript
function f() {
    return Promise.reject('Error');
}

// asyncF is equivalent to f!
async function asyncF() {
    throw 'Error';
}
```

```javascript
let fn = async function() {
    throw 'reject';
}
fn().catch(err => console.log(err));    // reject
```

## await

await 用来等待一个 promise 对象，它只能在异步函数 async function 中使用。

await 后跟的如果不是 promise 对象会被转化成 promise 对象。

```javascript
let foo = async function() {
    await Promise.reject(1);
}

foo().catch(err => console.log(err))    // 1
```

```javascript
let bar = async function() {
    try {
        await Promise.reject('error')
    } catch(e) {
        console.log(e)
    }
}
```

```javascript
let foo = async function() {
    return await 1;
}

foo().then(obj => console.log(obj));    // 1
```

```javascript
let bar = async function() {
    return await new Promise(resolve => {
        setTimeout(() => resolve('hello world'),1000)
    });
}

bar().then(src => console.log(src));
```

```javascript
function resolveAfter2Seconds(x) { 
    return new Promise(resolve => {
        setTimeout(() => {
            resolve(x);
        }, 2000);
    });
}

async function f1() {
    var x = await resolveAfter2Seconds(10);
    console.log(x); // 10
}

f1();
```

```javascript
async function example() {
    const r1 = await new Promise(resolve =>
        setTimeout(resolve, 500, 'slowest')
    )
    const r2 = await new Promise(resolve =>
        setTimeout(resolve, 200, 'slow')
    )
    return [r1, r2]
}

example().then(result => console.log(result))
// ['slowest', 'slow']
```

```javascript
function delay(time) {
  return new Promise((resolve,reject) => {
    setTimeout(()=>{
      if(Math.random()>0.8){
        resolve(time)
      }else{
        reject('error..')
      }
    }, time)
  })
}

async function fn() {
  console.log('start')
  let time = await delay(1000)
  console.log(`${time}ms passed`)
  let time2 = await delay(3000)
  console.log(`${time2}ms passed`)
}

fn().catch(err=>console.log(err))
````