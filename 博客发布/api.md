splice:切除

语法:

```js
array.splice(start[, deleteCount[, item1[, item2[, ...]]]])
```

start:起始下标

deleteCount:插入位置的后续删除项

item:项目名





## Function.prototype.call()

定义:这个方法会传递指定的this,和参数来调用函数

语法:

```js
function.call(thisArg, arg1, arg2, ...)
```

`thisArg`

可选的。在 *`function`* 函数运行时使用的 `this` 值。请注意，`this`可能不是该方法看到的实际值：如果这个函数处于[非严格模式](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Strict_mode)下，则指定为 `null` 或 `undefined` 时会自动替换为指向全局对象，原始值会被包装。

`arg1, arg2, ...`

指定的参数列表。

