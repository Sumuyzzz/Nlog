### new的实质



```js
function _new(Constructor,...arg) {
	let	instance = Object.create(Constructor.prototype)
	Constructor.apply(instance,arg)
	return instance
}

```

