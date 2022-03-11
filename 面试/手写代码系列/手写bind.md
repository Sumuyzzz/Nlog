## Bind

```js
function.bind(thisArg[, arg1[, arg2[, ...]]])
```

参数：

* `thisArg`：作为this绑定的值。
* `arg1`:具体参数

返回值：

返回一个原函数的拷贝，并拥有指定this值和参数



#### 简单版
思路：bind接收两个参数，分别为context和argument，返回一个使用apply绑定this的函数
```js
Function.prototype.myBind = function(context, ...argument) {
    const fn = this
    return function() {
        return fn.apply(context, argument)
    }
}
```


#### 完整版
思路：如果直接调用抛出错误，如果是构造函数就使用new
```js
Function.prototype.myBind = function(context, ...arg1) {
    if (this === Function.prototype) {
        throw new Error('Error')
    }
    const fn = this
    return function Fn(...arg2) {
        if (this instanceof Fn) {
            return new fn(...args1,...args2)
        }
        return fn.apply(context, arg1.concat(arg2))
    }
}
```
