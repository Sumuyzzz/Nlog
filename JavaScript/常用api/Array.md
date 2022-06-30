**！**：表示理解可能有误

# 返回新数组
## Array.prototype.concat()
>合并两个或多个数组

```js
const array1 = ['a', 'b', 'c'];
const array2 = ['d', 'e', 'f'];
const array3 = array1.concat(array2);
console.log(array3); //["a", "b", "c", "d", "e", "f"]
```
## Array.prototype.entries()
>返回一个可迭代的对象，该对象包含键值对

```js
const array1 = ['a', 'b', 'c'];

const iterator1 = array1.entries();

console.log(iterator1.next())
//Object { value: Array [0, "a"], done: false }

console.log(iterator1.next().value);

// Array [1, "b"]
```
## Array.prototype.every()
>表示所有元素是否满足条件，返回所有值

```js
const isBelowThreshold = (currentValue) => currentValue < 40;

const array1 = [1, 30, 39, 29, 10, 13];

console.log(array1.every(isBelowThreshold));//true
```

## Array.prototype.filter()
>返回一个满足条件的新数组

```js
const words = ['spray', 'limit', 'elite', 'exuberant', 'destruction', 'present'];

const result = words.filter(word => word.length > 6);

console.log(result);["exuberant", "destruction", "present"]
```
## Array.prototype.find()
> 返回第一个满足条件的元素

```js
const array1 = [5, 12, 8, 130, 44];

const found = array1.find(element => element > 10);

console.log(found);
// 12

```

## Array.prototype.findIndex()
>返回第一个满足条件的索引

```js
const array1 = [5, 12, 8, 130, 44];

const isLargeNumber = (element) => element > 13;

console.log(array1.findIndex(isLargeNumber)); //3
```

## Array.prototype.flat()
>根据参数去掉，嵌套数组层数，返回一个新的数组，**默认值为1**

```js
const arr1 = [0, 1, 2, [3, 4]];
console.log(arr1.flat()); //[0, 1, 2, 3, 4]

const arr2 = [0, 1, 2, [[[3, 4]]]];

console.log(arr2.flat(2)); //[0, 1, 2, [3, 4]]
```
## Array.prototype.forEach()
> 接收一个函数，函数和元素遍历执行

```js
const array1 = [1,2,3,4,5];

const nullArray =[]

array1.forEach(i => nullArray.push(i*4) );

console.log(array1) //[1,2,3,4,5]

console.log(nullArray) //[4, 8, 12, 16, 20]
```
## Array.from()
>


# 更改原数组
## ！Array.prototype.copyWithin() 
>拷贝某一段数组，替换到原数组，个数不改变

**copyWithin(target)**：从目标索引开始替换

**copyWithin(start,end)**：拷贝起始值到结束值的数组

```js

const array1 = [1,2,3,4,5,6,7,8,9];

console.log(array.copyWithin(3));

//[1, 2, 3, 1, 2, 3, 4, 5, 6]


console.log(array.copyWithin(1,3));

//[1, 4, 5, 6, 7, 8, 9, 8, 9]



```

## Array.prototype.fill()
>根据传入参数，自动填满数组

```js
const array1 = [1, 2, 3, 4, 5, 6, 7, 8, 9, 0];

console.log(array1.fill(0, 2, 4));//[1, 2, 0, 0, 5, 6, 7, 8, 9, 0]

console.log(array1.fill(5, 1));//[1, 5, 5, 5, 5, 5, 5, 5, 5, 5]

console.log(array1.fill(6)) //[6, 6, 6, 6, 6, 6, 6, 6, 6, 6]


```

