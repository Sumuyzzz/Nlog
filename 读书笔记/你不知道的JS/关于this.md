## 为什么要用this

```js
function identify() {
return this.name.toUpperCase();
}
function speak() {
var greeting = "Hello, I'm " + identify.call( this );
console.log( greeting );
}
var me = {
name: "Kyle"
};
var you = {
name: "Reader"
};
identify.call( me ); // KYLE
identify.call( you ); // READER
speak.call( me ); // Hello, 我是 KYLE
speak.call( you ); // Hello, 我是 READER
```

这段代码可以在不同的上下文对象（me 和 you）中重复使用函数 identify() 和 speak()， 不用针对每个对象编写不同版本的函数。



如果不使用 this，那就需要给 identify() 和 speak() 显式传入一个上下文对象。

```js
function identify(context) {
return context.name.toUpperCase();
}
function speak(context) {
var greeting = "Hello, I'm " + identify( context );
console.log( greeting );
}
identify( you ); // READER
speak( me ); //hello, 我是 KYLE
```

随着你的使用模式越来越复杂，显式传递上下文对象会让代码变得越来越混乱，使用 this 则不会这样。当我们介绍对象和原型时，你就会明白函数可以自动引用合适的上下文对象 有多重要。







## 误解

### 指向自身

```js
function foo(num) {
console.log( "foo: " + num );
// 记录 foo 被调用的次数
this.count++;
}
foo.count = 0;
var i;
for (i=0; i<10; i++) {
if (i > 5) {
foo( i );
}
}
// foo: 6
// foo: 7
// foo: 8
// foo: 9
// foo 被调用了多少次？
console.log( foo.count ); // 0 -- WTF
```

显然从字面意思来理解 this 是错误的。

### 它的作用域











**学习 this 的第一步是明白 this 既不指向函数自身也不指向函数的词法作用域。**

**this 实际上是在函数被调用时发生的绑定，它指向什么完全取决于函数在哪里被调用。**









## 绑定规则

默认绑定

独立的函数调用

非严格模式会默认绑定全局对象，浏览器全局对象也就是widow

```js
function foo() {
console.log( this.a );
}
var a = 2;
foo(); // 2


function foo() {
"use strict";
console.log( this.a );
}
var a = 2;
foo(); // TypeError: this is undefined
```





隐式绑定

