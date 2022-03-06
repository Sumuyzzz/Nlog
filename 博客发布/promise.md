## 回调地狱



问题:

### 1.难以复用

回调的顺序确定下来之后，想对其中的某些环节进行复用也很困难，牵一发而动全身

### 2.堆栈信息被断开



### 3.借助外层变量



**之所以单独讲讲回调地狱，其实是想说嵌套和缩进只是回调地狱的一个梗而已，它导致的问题远非嵌套导致的可读性降低而已。**





## Promise





### Promise.all

Promise.all 方法接收一个promise的iterable类型（注：Array，Map，Set都属于ES6的iterable类型）的输入，并且只返回一个[`Promise`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Promise)实例， 那个输入的所有promise的resolve回调的结果是一个数组

