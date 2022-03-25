```js

function myInstanceof(target, constructor){
	
	let left = Object.getPrototypeOf(target)

	let right = constructor.prototype
	
	while(true){
		if(left===null){
			return false
		}
		if(left ===right){
			return  true
		}
		left = Object.getPrototypeOf(left)
	}
}


```