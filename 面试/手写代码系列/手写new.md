### new的实质

虽然很多人都已经了解了new的实质，那么我还是要再说一下new 的实质
 `var o = new Object()`

1. 新建一个对象o
2. `o. __proto__ = Object.prototype` 将新创建的对象的`__proto__`属性指向构造函数的`prototype`
3. 将this指向新创建的对象
4. 返回新对象，但是这里需要看构造函数有没有返回值，如果构造函数的返回值为基本数据类型`string,boolean,number,null,undefined`,那么就返回新对象，如果构造函数的返回值为对象类型，那么就返回这个对象类型





```js
function create(){
    let obj = new Object()
    let constructor = [].shift.call(arguments)
    obj._proto_ = constructor.prototype
    let result = constructor.apply(obj.arguments)
    return typeof result == ''
}
```

