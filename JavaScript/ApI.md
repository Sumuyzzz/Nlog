#### floor()

### Function.prototype.apply()

**`apply()`** 方法调用一个具有给定`this`值的函数，以及以一个数组（或[类数组对象](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Guide/Indexed_collections#working_with_array-like_objects)）的形式提供的参数。

语法

```js
func.apply(thisArg, [argsArray])
```

**thisArg**

在 *`func`* 函数运行时使用的 `this` 值。必选的。

**argsArray**

一个数组或者类数组对象，其中的数组元素将作为单独的参数传给 `func` 函数。可选的

### 示例

```js
var array = ['a', 'b'];
var elements = [0, 1, 2];
array.push.apply(array, elements);
console.info(array); // ["a", "b", 0, 1, 2]
```





### slice()

`**slice()**` 方法返回一个新的数组对象，这一对象是一个由 `begin` 和 `end` 决定的原数组的**浅拷贝**（包括 `begin`，不包括`end`）。原始数组不会被改变。

语法:

```js
arr.slice([begin[, end]])
```

`begin` **可选**

起始值下标.如果为负数,会从数组倒数位置开始算起





例子

```js
const animals = ['ant', 'bison', 'camel', 'duck', 'elephant'];

console.log(animals.slice(2));
// expected output: Array ["camel", "duck", "elephant"]

console.log(animals.slice(2, 4));
// expected output: Array ["camel", "duck"]

console.log(animals.slice(1, 5));
// expected output: Array ["bison", "camel", "duck", "elephant"]

console.log(animals.slice(-2));
// expected output: Array ["duck", "elephant"]

console.log(animals.slice(2, -1));
// expected output: Array ["camel", "duck"]

```











ceil()

parseInt()

split()

every()

`**every()**` 方法测试一个数组内的所有元素是否都能通过某个指定函数的测试。它返回一个布尔值。

语法

```js
arr.every(callback(element[, index[, array]])[, thisArg])
```

