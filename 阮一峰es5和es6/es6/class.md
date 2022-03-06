## 由来

ES6 的`class`可以看作只是一个语法糖

```javascript
function Point(x, y) {
  this.x = x;
  this.y = y;
}

Point.prototype.toString = function () {
  return '(' + this.x + ', ' + this.y + ')';
};

var p = new Point(1, 2);


//通过class改写
class Point {
  constructor(x, y) {
    this.x = x;
    this.y = y;
  }

  toString() {
    return '(' + this.x + ', ' + this.y + ')';
  }
}
```

另外，类的内部所有定义的方法，都是不可枚举的（non-enumerable）。





### constructor

`constructor()`方法是类的默认方法，通过`new`命令生成对象实例时，自动调用该方法。**一个类必须有`constructor()`方法，**如果没有显式定义，一个空的`constructor()`方法会被默认添加。

```javascript
class Point {
}

// 等同于
class Point {
  constructor() {}
}
```

`constructor()`方法默认返回实例对象（即`this`），完全可以指定返回另外一个对象。

```js
class Foo {
  constructor() {
    return Object.create(null);
  }
}

new Foo() instanceof Foo
// false
```

`constructor()`函数返回一个全新的对象,结果导致实例对象不是`Foo`类的实例。

**类必须使用`new`调用，否则会报错。**

### 实例

实例的属性除非显式定义在其本身（即定义在`this`对象上），否则都是定义在原型上（即定义在`class`上）。

```js
//定义类
class Point {

  constructor(x, y) {
    this.x = x; //this绑定实例，所以有
    this.y = y;
  }

  toString() {
    return '(' + this.x + ', ' + this.y + ')';
  }

}

var point = new Point(2, 3);

point.toString() // (2, 3)

point.hasOwnProperty('x') // true
point.hasOwnProperty('y') // true
point.hasOwnProperty('toString') // false
point.__proto__.hasOwnProperty('toString') // true
```

### 取值函数（getter）和存值函数（setter）

```js
let 
```







## 静态方法

在方法前面加上`static`关键字，表示该方法不会被实例继承







## 注意点

1. **严格模式**

类和模块的内部，默认就是严格模式，所以不需要使用`use strict`指定运行模式。

2. **不存在提升**
3. **name 属性**









如果子类没有定义`constructor`方法，这个方法会被默认添加，代码如下。也就是说，不管有没有显式定义，任何一个子类都有`constructor`方法。

```js
class ColorPoint extends Point {
}

// 等同于
class ColorPoint extends Point {
  constructor(...args) {
    super(...args);
  }
 }
```







在子类的构造函数中，**只有调用`super`之后**，才可以使用`this`关键字，否则会报错。这是因为子类实例的构建，基于父类实例，只有`super`方法才能调用父类实例。

```js
class Point {
  constructor(x, y) {
    this.x = x;
    this.y = y;
  }
}

class ColorPoint extends Point {
  constructor(x, y, color) {
    this.color = color; // ReferenceError
    super(x, y);
    this.color = color; // 正确
  }
}
```



派生类定义默认提供构造器

```js
class B extends A {
    
}
//相当于
class B extends A{
    construstor(...args){
        super(..args)
    }
}
```

> 1. 只能在派生类中使用super()
> 2. 在This使用之前调用super()
> 3. 唯一能避免调用 super() 的办法，是从类构造器中返回一个对象。



`extends`关键字后面可以跟多种类型的值。

```js
class B extends A {
}
```

上面代码的`A`，只要是一个有`prototype`属性的函数，就能被`B`继承。由于函数都有`prototype`属性（除了`Function.prototype`函数）

**因此`A`可以是任意函数。**







派生类定义同名方法，屏蔽自身方法实现

```js
class Square extends Rectangle {
constructor(length) {
super(length, length);
}
// 重写、屏蔽并调用了 Rectangle.prototype.getArea()
getArea() {
return super.getArea();
}
}//
```

