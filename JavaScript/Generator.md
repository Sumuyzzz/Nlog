## 介绍

Generator函数返回一个可迭代的对象，是一个状态机，封装多种状态。

特点：
* 在`function`关键字与函数名之间有个`*`号
* 函数体内部使用`yield`表达式来生成特定值

## 使用
```js
function *generateSequence() {
    yield 1;
    yield 2;
    return 3; //后面的4不会生成
    yield 4;
}

let generator = generateSequence();

let one = generator.next();

one //{value:1,done:false}
```
 使用函数声明和`*`来声明一个生成器函数，调用方式和普通函数没区别，不同的是，函数并不执行，返回的也不是执行结果，而是一个指向内部状态的指针对象，也就是**Iterator Object**

当使用`next`方法时，会将指针指向下个状态，也就是说，每次使用`next`方法，都会从上个指针开始执行，直到遇到`yield`表达式为止。

总之，Generator 函数是分段执行的，`yield`表达式是暂停执行的标记，而`next`方法可以恢复执行。




### yield
`generator`函数调用返回一个可迭代对象，使用`next`方法来遍历对象的状态，`generator`函数内部就需要使用`yield`表达式来暂停`next`方法执行。










### next
每次调用`next`方法，都会返回`yield`生成的值。


参考

[# Generator 函数的语法](https://wangdoc.com/es6/generator.html)