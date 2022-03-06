## 会改变数组的方法

### push

概述：会在数组的末端添加一个或多个元素，并返回添加新元素后的**数组长度**。**会改变原数组。**

```js
const animals = ['pigs', 'goats', 'sheep'];

const count = animals.push('cows');
console.log(count); //4

console.log(animals); //["pigs", "goats", "sheep", "cows"]
```

***

### pop

概述：数组中删除最后一个元素，并返回该元素的值。**会改变原数组。**



shift

unshift

splice

slice

concat

不会改变自身数组的方法







## 高阶函数

### Array.prototype.map

概述：会创建一个新的数组，遍历原数组的元素，调用函数得到新的值。**不会改变原数组**

```js
const arr1 = [1, 2, 3, 4];
const arr2 = arr1.map(item => item * 2);

console.log( arr2 );
// [2, 4, 6, 8]
console.log( arr1 );
// [1, 2, 3, 4]
```

### Array.prototype.filter

概述：创建一个新的方法，根据条件得到新的值。**不会改变原数组**

```js
const arr1 = [1, 2, 1, 2, 3, 5, 4, 5, 3, 4, 4, 4, 4];
const arr2 = arr1.filter( (element, index, self) => {
    return self.indexOf( element ) === index;
});

console.log( arr2 );
// [1, 2, 3, 5, 4]
console.log( arr1 );
// [1, 2, 1, 2, 3, 5, 4, 5, 3, 4, 4, 4, 4]
```

### Array.prototype.reduce

概述：
