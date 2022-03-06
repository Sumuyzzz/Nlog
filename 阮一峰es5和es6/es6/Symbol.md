## 什么是Symbol

* 第**6**种原始数据类型
* 表示独一无二的值
* `Symbol`函数前不能使用`new`命令,因为他不是由Object生成的，也不能添加属性



```js
const sym1 = Symbol();
const sym2 = Symbol();

console.log(sym1 === sym2) //false
```

创建 Symbol 的时候，可以添加一个描述。

通过使用`description`，可以访问这个描述信息

```js
const sym = Symbol('foo');

sym.description // "foo"
```

