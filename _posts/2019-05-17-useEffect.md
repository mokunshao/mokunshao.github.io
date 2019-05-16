---
title: UseEffect
---

### useEffect

componentDidMount 是用于在 mount 过程结束的副作用

componentDidUpdate 是用于在 update 过程结束的副作用

useEffect = componentDidMount + componentDidUpdate

### useEffect 模拟 componentDidMount

```javascript
useEffect(()=>{
// 每次 mount 或者 update 都会调用这里
})
```

```javascript
useEffect(()=>{
// 只有 mount 时会调用这里
},[])
```

### useEffect 模拟 componentDidUnmount

```javascript
useEffect(()=>{
// 只有 mount 时会调用这里
	return ()=>{
		// 只有 unmount 时会调用这里
	}
},[])
```

### useEffect 模拟 componentDidUpdate

```javascript
const mounted = useRef();
useEffect(()=>{
	if(!mounted.current){
		mounted.current = true;
	}else{
		// do componentDidUpdate logic
	}
})
```