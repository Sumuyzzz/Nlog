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

	function Dog(name){
	this.name = name 
	}

```


##  直接调用
严格模式下，undefined
非严格模式，默认指向window
```js
fnc() //'window'
```

## 对象调用
指的是对象
```js
obj.func() //obj
```



## 构造函数
指的是实例
```js


let blackDog = new Dog('black')
let whileDog = new Dog('while')



```

[# Reference Type](https://zh.javascript.info/reference-type)