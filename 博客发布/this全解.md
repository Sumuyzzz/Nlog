##  揭秘 "this"

#### 什么是this

> 就是调用这个方法的对象



`this` 建立在四个规则上：默认绑定、隐式绑定、显式绑定和 “new”绑定。





默认绑定：直接执行，默认是`undefined`，浏览器默认是`window`，node默认是`global`

隐式绑定：对象的方法，`this`指的就是这个对象

显式绑定：通过使用`call`,`apply`,`bind`方法，传入的第一个参数就是`this`

new绑定：`this`就是new生成的对象实例



## 如何确定this的值

1.计算 MemberExpression 的结果赋值给 ref

2.判断 ref 是不是一个 Reference 类型

> 2.1 如果 ref 是 Reference，并且 IsPropertyReference(ref) 是 true, 那么 this 的值为 GetBase(ref)
>
> 2.2 如果 ref 是 Reference，并且 base value 值是 Environment Record, 那么this的值为 ImplicitThisValue(ref)
>
> 2.3 如果 ref 不是 Reference，那么 this 的值为 undefined



### 分析

1. 计算 MemberExpression 的结果赋值给 ref

什么是 MemberExpression？看规范 11.2 Left-Hand-Side Expressions：

MemberExpression :

- PrimaryExpression // 原始表达式 可以参见《JavaScript权威指南第四章》
- FunctionExpression // 函数定义表达式
- MemberExpression [ Expression ] // 属性访问表达式
- MemberExpression . IdentifierName // 属性访问表达式
- new MemberExpression Arguments // 对象创建表达式

```js
function foo() {
    console.log(this)
}

foo(); // MemberExpression 是 foo

function foo() {
    return function() {
        console.log(this)
    }
}

foo()(); // MemberExpression 是 foo()

var foo = {
    bar: function () {
        return this;
    }
}

foo.bar(); // MemberExpression 是 foo.bar
```



所以简单理解 MemberExpression 其实就是()左边的部分。

2. 判断 ref 是不是一个 Reference 类型。

例子

```js
var value = 1;

var foo = {
  value: 2,
  bar: function () {
    return this.value;
  }
}

//示例1
console.log(foo.bar());
//示例2
console.log((foo.bar)());
//示例3
console.log((foo.bar = foo.bar)());
//示例4
console.log((false || foo.bar)());
//示例5
console.log((foo.bar, foo.bar)());
```







