### 什么是generator

生成器（ generator ）是能返回一个迭代器的函数。

表示方法：**function 关键字之 后的一个星号（ * ）来表示，并能使用新的 yield 关键字。将星号紧跟在 function 关键 字之后，或是在中间留出空格，都是没问题的**

```js
function *createIterator() {
yield 1;
yield 2;
yield 3;
}
// 生成器能像正规函数那样被调用，但会返回一个迭代器
let iterator = createIterator();
console.log(iterator.next().value); // 1
console.log(iterator.next().value); // 2
console.log(iterator.next().value); // 3
```

**生成器函数最有意思的方面可能就是它们会在每个 yield 语句后停止执行。**



>  不能将箭头函数创建为生成器。

