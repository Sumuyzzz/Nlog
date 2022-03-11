## Apply

```js
func.apply(thisArg, [argsArray])
```

#### 实现
##### 完整版
思路：接收context和arg参数列表，
```js
Function.prototype.myApply = function(context, ...args) {
    context = context || window
    context.fn = this
    let result
    if (Array.isArray(args)) {
        result = context.fn(...args)
    } else {
        result = context.fn()
    }
    delete context.fn
    return result
}
```

