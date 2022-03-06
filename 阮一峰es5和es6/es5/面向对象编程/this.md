## 含义

`this`都有一个共同点：它总是返回一个对象。

`this`就是属性或方法“当前”所在的对象。

```js
this.property
```

上面代码中，`this`就代表`property`属性当前所在的对象。



**总结：**

* JavaScript 语言之中，一切皆对象，**运行环境也是对象**，所以函数都是在**某个对象之中运行**，**`this`就是函数运行时所在的对象（环境）**。

## 实质

this的设置目的是为了指**当前运行环境**

## 使用场合

1. **全局环境**
   1. node默认global，浏览器默认window
2. **构造函数**
   1. 指向实例
3. **对象的方法**
   1. 当前对象

## 注意场景

### 避免多层 this

```js
var o = {
  f1: function () {
    console.log(this);
    var f2 = function () {
      console.log(this);
    }();
  }
}

o.f1()
// Object
// Window
```

上面代码实质是

```js
function tmp() {
      console.log(this);
    }
var o = {
  f1: function () {
    console.log(this);
    var f2 = tmp();
  }
}

o.f1()
```

问题在于，回调总是window在调用。

改写

```js
var o = {
  f1: function () {
    console.log(this);
      var that =this
    var f2 = function () {
      console.log(that);
    }();
  }
}

//或者

var o = {
  f1: function () {
    console.log(this);
    var f2 = function () {
      console.log(this);
    }.call(this);
  }
}
```

### 避免数组处理方法中的 this

数组的`map`和`foreach`方法，允许提供一个函数作为参数。这个函数内部不应该使用`this`。

```js
var o = {
  v: 'hello',
  p: [ 'a1', 'a2' ],
  f: function f() {
    this.p.forEach(function (item) {
      console.log(this.v + ' ' + item);
    });
  }
}

o.f()
// undefined a1
// undefined a2
```

这里的`this.v`实质是`window.v`，原因在于，forEach执行的是回调函数

改写

```js
//使用that代替this
var o = {
  v: 'hello',
  p: [ 'a1', 'a2' ],
  f: function f() {
      var that = this
    this.p.forEach(function (item) {
      console.log(that.v + ' ' + item);
    });
  }
}
o.f()
// hello a1
// hello a2

//使用forEach的第二参数
var o = {
  v: 'hello',
  p: [ 'a1', 'a2' ],
  f: function f() {
    this.p.forEach(function (item) {
      console.log(this.v + ' ' + item);
    },this);
  }
}
o.f()
// hello a1
// hello a2
```

### 避免回调函数中的 this

```js
var o = new Object();
o.f = function () {
  console.log(this === o);
}

// jQuery 的写法
$('#button').on('click', o.f);

//false
```

原因是此时`this`不再指向`o`对象，而是指向**按钮的 DOM 对象**，因为`f`方法是在**按钮对象的环境中被调用的**

## 绑定 this 的方法

### Function.prototype.call()

```js
var obj = {
   f : function () {
  return this;
}
};


obj.f()  //obj
obj.f.call(obj) //obj

obj.f.call() //window
obj.f.call(null) //window
obj.f.call(undefined) //window
```





`call`方法的参数，应该是一个对象。如果参数为空、`null`和`undefined`，则默认传入全局对象。

```js
var obj = {
   f : function () {
  return this;
}
};

obj.f()  //obj
obj.f.call(obj) //obj

obj.f.call() //window
obj.f.call(null) //window
obj.f.call(undefined) //window
obj.f.call(window) //window
```

### Function.prototype.apply()

`apply`方法的作用与`call`方法类似，也是改变`this`指向，然后再调用该函数。唯一的区别就是，它接收一个数组作为函数执行时的参数，使用格式如下。

```js
func.apply(thisValue, [arg1, arg2, ...])
```

#### 有趣的应用。

1. **找出数组最大元素**	

  ```js
      var a = [10, 2, 4, 15, 9];
      Math.max.apply(null, a) // 15
  ```

2. **将数组的空元素变为`undefined`**

 ```js
   Array.apply(null, ['a', ,'b'])
   // [ 'a', undefined, 'b' ]
 ```
   空元素与undefined的差别在于，数组的forEach方法会跳过空元素，但是不会跳过undefined。因此，遍历内部元素的时候，会得到不同的结果。

```js
var a = ['a', , 'b'];

function print(i) {
  console.log(i);
}

a.forEach(print)
// a
// b

Array.apply(null, a).forEach(print)
// a
// undefined
// b
```

3. **转换类似数组的对象**
```js
Array.prototype.slice.apply({0: 1, length: 1}) // [1]
Array.prototype.slice.apply({0: 1}) // []
Array.prototype.slice.apply({0: 1, length: 2}) // [1, undefined]
Array.prototype.slice.apply({length: 1}) // [undefined]
```

4. **绑定回调函数的对象**

 ```js
 var o = new Object();
 
 o.f = function () {
   console.log(this === o);
 }
 
 var f = function (){
   o.f.apply(o);
   // 或者 o.f.call(o);
 };
 
 // jQuery 的写法
 $('#button').on('click', f);
 ```

   改写之前的例子

### Function.prototype.bind()

`bind()`方法用于将函数体内的`this`绑定到某个对象，然后返回一个新函数。

`bind`方法的参数就是所要绑定`this`的对象，下面是一个更清晰的例子。

```js
var counter = {
  count: 0,
  inc: function () {
    this.count++;
  }
};

var func = counter.inc.bind(counter);
func();
counter.count // 1
```

注意：

1. **每一次返回一个新函数**

```js
element.addEventListener('click', o.m.bind(o));

element.removeEventListener('click', o.m.bind(o));
```

由于每次生成的匿名函数都不是同一个函数，所以无法取消绑定

正确写法

```js
var listener = o.m.bind(o);
element.addEventListener('click', listener);
//  ...
element.removeEventListener('click', listener);
```

将函数地址存储在变量里，通过变量获取同一个回调函数

2. **结合回调函数使用**
