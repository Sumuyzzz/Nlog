## 概述

Promise 对象是 JavaScript 的异步操作解决方案，为异步操作提供统一接口。

它起到**代理作用（proxy），充当异步操作与回调函数之间的中介，使得异步操作具备同步操作的接口**。



首先，Promise 是一个对象，也是一个构造函数。

```js
function f1(resolve, reject) {
  // 异步代码...
}

var p1 = new Promise(f1);
```

上面代码中，`Promise`构造函数接受一个回调函数`f1`作为参数，`f1`里面是异步操作的代码。然后，返回的`p1`就是一个 Promise 实例。

Promise 实例有一个`then`方法，用来指定下一步的回调函数。

```js
var p1 = new Promise(f1);
p1.then(f2);
```

## Promise 对象的状态

Promise 对象通过自身的状态，来控制异步操作。Promise 实例具有三种状态。

- 异步操作未完成（pending）
- 异步操作成功（fulfilled）
- 异步操作失败（rejected）
- 上面三种状态里面，`fulfilled`和`rejected`合在一起称为`resolved`（已定型）

这三种的状态的变化途径只有两种。

- 从“未完成”到“成功”
- 从“未完成”到“失败”

因此，Promise 的最终结果只有两种。

- 异步操作成功，Promise 实例传回一个值（value），状态变为`fulfilled`。
- 异步操作失败，Promise 实例抛出一个错误（error），状态变为`rejected`。

## Promise 构造函数

JavaScript 提供原生的`Promise`构造函数，用来生成 Promise 实例

```js
var promise = new Promise(function (resolve, reject) {
  // ...

  if (/* 异步操作成功 */){
    resolve(value);
  } else { /* 异步操作失败 */
    reject(new Error());
  }
});
```

`resolve`函数的作用是，将`Promise`实例的状态从“未完成”变为“成功”（即从`pending`变为`fulfilled`），在异步操作成功时调用，并将异步操作的结果，作为参数传递出去。`reject`函数的作用是，将`Promise`实例的状态从“未完成”变为“失败”（即从`pending`变为`rejected`），在异步操作失败时调用，并将异步操作报出的错误，作为参数传递出去。

```js
function timeout(ms) {
  return new Promise((resolve, reject) => {
    setTimeout(resolve, ms, 'done');
  });
}

timeout(100)
```

上面代码中，`timeout(100)`返回一个 Promise 实例。100毫秒以后，该实例的状态会变为`fulfilled`。

## Promise.prototype.then()

## 小结

优点：

* 让回调函数变成了规范的链式写法，程序流程可以看得很清楚
* 可以实现许多强大的功能，比如同时执行多个异步操作，等到它们的状态都改变以后，再执行一个回调函数；
* 为多个回调函数中抛出的错误，统一指定处理方法
* 它的状态一旦改变，无论何时查询，都能得到这个状态。

## 微任务

Promise 的回调函数属于异步任务，会在同步任务之后执行。

