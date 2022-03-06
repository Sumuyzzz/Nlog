## Generator（生成器）

概念：

* 语法上，首先可以把它理解成，Generator 函数是一个状态机，封装了多个内部状态。执行 Generator 函数会返回一个遍历器对象，返回的遍历器对象，可以依次遍历 Generator 函数内部的每一个状态。

* 形式上，Generator 函数是一个普通函数，但是有两个特征。

  1. `function`关键字与函数名之间有一个星号

  2. 函数体内部使用`yield`表达式，定义不同的内部状态（`yield`在英语里的意思就是“产出”）。



```js
function* helloWorldGenerator() {
  yield 'hello';
  yield 'world';
  return 'ending';
  yield 'hello';
  yield 'world';
}

var hw = helloWorldGenerator();
```

然后，Generator 函数的调用方法与普通函数一样，也是在函数名后面加上一对圆括号。不同的是，调用 Generator 函数后，**该函数并不执行，返回的也不是函数运行结果，而是一个指向内部状态的指针对象，也就是上一章介绍的遍历器对象（Iterator Object）。**

使用next方法可以，使得指针移向下一个状态。也就是，每次执行都会指向下一个状态。

换言之，Generator 函数是分段执行的，`yield`表达式是暂停执行的标记，而`next`方法可以恢复执行。



**总结**

调用 Generator 函数，返回一个遍历器对象，代表 Generator 函数的内部指针。以后，每次调用遍历器对象的`next`方法，就会返回一个有着`value`和`done`两个属性的对象。`value`属性表示当前的内部状态的值，是`yield`表达式后面那个表达式的值；`done`属性是一个布尔值，表示是否遍历结束。

```js
function * foo(x, y) { ··· }
function *foo(x, y) { ··· }
function* foo(x, y) { ··· }
function*foo(x, y) { ··· }
```

支持4种写法，一般用第二种（看个人习惯）





