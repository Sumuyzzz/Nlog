## call
```js
function.call(thisArg, arg1, arg2, ...)
```

```js
Function.prototype.myCall = function (context, ...args){
    let object = context || window
    object.fn = this
    let result = object.fn(...args)
    delete context.fn
    return result
}
```

实现步骤：传入`context`对象和实际参数，使用对象绑定函数并调用，删除对象方法，并反对结果。












