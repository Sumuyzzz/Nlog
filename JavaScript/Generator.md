## 介绍

Generator函数返回一个可迭代的对象，是一个状态机，封装多种状态。

特点：
* 在`function`关键字与函数名之间有个`*`号
* 函数体内部使用`yield`表达式来生成特定值


### yield
`generator`函数调用返回一个可迭代对象，使用`next`方法来遍历对象的状态，`generator`函数内部就需要使用`yield`表达式来暂停`next`方法执行。

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
