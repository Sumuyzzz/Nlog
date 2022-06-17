判断this如下：

* 直接调用（严格模式：`undefined`，非严格：`window`）
* 对象调用（对象）
* 构造函数（`new` 出来的实例）
* 箭头函数（无自身`this` ，通过作用域链获取上层`this`）
* 使用`call`/`apply`/`bind`绑定（第一个参数）
* 事件绑定的函数（侦听的dom元素）







[Reference Type](https://zh.javascript.info/reference-type)
[30s code](https://www.30secondsofcode.org/articles/s/javascript-this)