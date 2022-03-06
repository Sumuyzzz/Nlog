## call

`call()` 方法使用一个指定的 `this` 值和单独给出的一个或多个参数来调用一个函数。

跟`apply()`类似，只有一个区别，就是 `call()` 方法接受的是**一个参数列表**，而 `apply()` 方法接受的是**一个包含多个参数的数组**。

```js
function.call(thisArg, arg1, arg2, ...)
```

```js
Function.prototype.myCall = function (context){
    let object = context || widow
    object.fn = this
    let args = [...arguments].slice(1)
    let result = object.fn(...args)
    delete context.fn
    return result
}
 
function fn1(){
    console.log(this)
}

let obj2 = {
    name : 'obj2'
}
fn1.myCall(obj2)

obj2.fn1()
```

实现步骤：

* 判断`context`是否是假值（0，null，undefined），不传值默认`window`
* 改变`This`指向,让这个函数对象执行`myCall`方法，这一步就是让`fn`的`This`指向`context`
* 接着拷贝`myCall`接收的实参，接着执行该函数，然后删除并返回结果。





## Apply

```js
func.apply(thisArg, [argsArray])
```

```js
Function.prototype.myApply = function (context) {
  var object = context || window
  object.fn = this
  var result
  // 需要判断是否存储第二个参数
  // 如果存在，就将第二个参数展开
  if (arguments[1]) {
    result = context.fn(...arguments[1])
  } else {
    result = context.fn()
  }
  delete context.fn
  return result
}

 
function fn1(){
    console.log(this)
}

let obj2 = {
    name : 'obj2'
}
fn1.myApply(obj2)


let obj2 = {
    name : 'obj2',
    fn1: function (){
        console.log(this)
    }
}
obj2.fn1()
delete obj2.fn1
```

实现步骤：

* 判断`context`是否是假值（0，null，undefined），不传值默认`window`
* 改变`This`指向,让这个函数对象执行`myCall`方法，这一步就是让`fn`的`This`指向`context`
* 判断输出结果，如果存在第二个参数，就把`arguments[1]`后面的值拷贝进`context.fn`里，否则直接执行
* 删除并返回结果



## Bind

```js
function.bind(thisArg[, arg1[, arg2[, ...]]])
```

参数：

* `thisArg`：作为this绑定的值。
* `arg1`:

返回值：

返回一个原函数的拷贝，并拥有指定this值和参数

```js
Function.prototype.myBind = function(){
    if(typeof this !== 'function'){
        throw new TypeError('Error')
    }
    let _this =this
let args = [...arguments].slice(1)
return function F (){
    if(this instanceof F){
		return new _this(...args,...argments)
    }
    return _this.apply(context,args.concat(...arguments))
  }
}

```







