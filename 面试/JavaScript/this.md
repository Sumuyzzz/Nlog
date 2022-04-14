## 概述
常见4种调用方式：
1. 直接调用
2. 对象调用
3. 构造函数使用new调用
4. 用call/apply/bind调用


### demo
```js
	let obj = {name:'obj',func:fuc}
	window.name = 'window'
	
	function fnc(){
	console.log(this.name)
	}
```


##  直接调用
```js
fnc() //'window'
```

## 对象调用

```js

obj.func() //obj
```






[# Reference Type](https://zh.javascript.info/reference-type)