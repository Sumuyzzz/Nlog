## 理解函数调用

内容介绍：

* 函数中的两个参数`arguments`和`this`
* 函数的调用方式
* 上下文问题



### arguments

定义：`arguments`参数是传递给函数的所有参数集合。属于伪数组

```js
function whatever(a, b, c){
    console.log('a:'+a)
    console.log('b:'+b)
    console.log('c:'+c)
    console.log('arg:'+arguments.length)
}

whatever(1, 2, 3, 4, 5)
 // a:1
 // b:2
 // c:3
 // arg:5
```

可以知道`arguments`的长度由传进去的实际参数个数所决定，也就是实参个数



使用场景：

```js
function sum() { ⇽- 一开始没有定义形式参数
var sum = 0;
for(var i = 0; i < arguments.length; i++){
sum += arguments[i];
} ⇽- 这里通过arguments获取传进来的参数进行迭代
return sum;
}
sum(1,3,4,5) <-- 可以传入任意参数
// 13
```









### 数组方法

处理集合的元素时，常常遇到需要知道数组的全部元素或部分元素 是否满足某些条件。



every



说明：如果所有数组 元素的回调结果都返回true时，every方法将返回true，否则返回false



用法：

```js
const ninjas = [
{name: "Yagyu", weapon: "shuriken"},
{name: "Yoshi" },
{name: "Kuma", weapon: "wakizashi"}
];

const allNinjasAreNamed = ninjas.every(ninja => "name" in ninja);
const allNinjasAreArmed = ninjas.every(ninja => "weapon" in ninja);
```



some



说明：当且仅当全部的回调函数都返回true时，every方法才返回 true，否则返回false。