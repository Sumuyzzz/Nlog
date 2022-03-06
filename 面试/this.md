### this指向、new关键字

`this`对象是是执行上下文中的一个属性，它指向最后一次调用这个方法的对象，在全局函数中，`this`等于`window`，而当函数被作为某个对象调用时，this等于那个对象。 在实际开发中，`this `的指向可以通过四种调用模式来判断。

1. 函数调用，当一个函数不是一个对象的属性时，直接作为函数来调用时，`this`指向全局对象。
2. 方法调用，如果一个函数作为一个对象的方法来调用时，`this`指向这个对象。
3. 构造函数调用，`this`指向这个用`new`新创建的实例。
4. 第四种是 `apply 、 call 和 bind `调用模式，这三个方法都可以显示的指定调用函数的 this 指向。`apply`接收参数的是数组，`call`接受参数列表，`` bind`方法通过传入一个对象，返回一个` this `绑定了传入对象的新函数。这个函数的 `this`指向除了使用`new `时会被改变，其他情况下都不会改变。

**new**

1. 首先创建了一个新的空对象
2. 设置原型，将对象的原型设置为函数的`prototype`对象。
3. 让函数的`this`指向这个对象，执行构造函数的代码（为这个新对象添加属性）
4. 判断函数的返回值类型，如果是值类型，返回创建的对象。如果是引用类型，就返回这个引用类型的对象。





```js
function foo () {
  console.log(this.a)
}
function doFoo (fn) {
  console.log(this)
  fn()
}
var obj = { a: 1, foo }
var a = 2
var obj2 = { a: 3, doFoo }

obj2.doFoo(obj.foo)

// { a:3, doFoo: f }
// 2

```

**如果你把一个函数当成参数传递到另一个函数的时候，也会发生隐式丢失的问题，且与包裹着它的函数的this指向无关。在非严格模式下，会把该函数的this绑定到window上，严格模式下绑定到undefined。**

回调函数，默认**undefined**





```js
var obj1 = {
  a: 1
}
var obj2 = {
  a: 2,
  foo1: function () {
    console.log(this.a)
  },
  foo2: function () {
    setTimeout(function () {
      console.log(this)
      console.log(this.a)
    }.call(obj1), 0)
  }
}
var a = 3
obj2.foo1()
obj2.foo2()


```

```js
obj2.foo2.call(obj1) 
//Window{...}
/3
```

**注意⚠️**：如果是这种写法的话，我改变的就是`foo2`函数内的`this`的指向了，但是我们知道，`foo2`函数内`this`的指向和`setTimeout`里函数的`this`是没有关系的，因为调用定时器的始终是`window`。



