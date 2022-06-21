传统es5写法，实现字符串包含字符判定功能

```js
function containsAll(haystack) {
 for (var i = 1; i < arguments.length; i++) { 
 var needle = arguments[i]; 
 if (haystack.indexOf(needle) === -1) {
 return false
    }
  }
    return true;
}

```

这里`var i=1`很重要，因为如果`arguments[0]`就是传进来第一个实参，也就是`haystack=第一个实参`，所以开始当循环的时候`needle === 第一个实参 `，接着就是根据的参数进行赋值判断

***

es6使用...扩展运算符和for...of实现

```js
function containsAll(haystack, ...needles) {
 for (var needle of needles) {
 if (haystack.indexOf(needle) === -1) {
 return false;
 }
 }
 return true;
}
```

`...needles`实际上等于除了`hastack`占用传进来的第一个参数，后续参数都会以`needles = [第二参数， 第三参数，后续参数]`变成可迭代对象

***

执行结果分析

```js
containsAll("banana", "b", "nan") //true
```

