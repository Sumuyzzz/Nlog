
用于构造函数生成实例，减少代码重复

简化一下操作
1. 生成一个空对象
2. 给空对象绑定原型和this
3. 执行构造函数，也就是给this附加属性
4. 返回this


```js

function newCreate(constructor,...arg) {

    let obj = Object.create(constructor.prototype)

    let result = constructor.apply(obj, arg)

    return typeof result === 'object' ? result : obj
}

```