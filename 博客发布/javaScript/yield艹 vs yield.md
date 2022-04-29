## yield 
简述：本质是关键字，用于暂停和恢复一个生成器函数
语法：
`[_rv_] = **yield** [_expression_];`

expression:定义的值
rv:传递给next()方法的可选值


例子：
```js
function* countAppleSales () {
  var saleList = [3, 7, 5];
  for (var i = 0; i < saleList.length; i++) {
    yield saleList[i];
  }
}

var appleStore = countAppleSales(); // Generator { }
console.log(appleStore.next()); // { value: 3, done: false }
console.log(appleStore.next()); // { value: 7, done: false }
console.log(appleStore.next()); // { value: 5, done: false }
console.log(appleStore.next()); // { value: undefined, done: true }



```




## yield*
简述：本质是表达式，用于委托给另一个可迭代对象
语法：
` yield* [[expression]];`


expression:返回一个可迭代的表达式

```js
function* g1() {
  yield 2;
  yield 3;
  yield 4;
}

function* g2() {
  yield 1;
  yield* g1();
  yield 5;
}

var iterator = g2();

console.log(iterator.next()); // { value: 1, done: false }
console.log(iterator.next()); // { value: 2, done: false }
console.log(iterator.next()); // { value: 3, done: false }
console.log(iterator.next()); // { value: 4, done: false }
console.log(iterator.next()); // { value: 5, done: false }
console.log(iterator.next()); // { value: undefined, done: true }
```




[# yield* MDN](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Operators/yield*)