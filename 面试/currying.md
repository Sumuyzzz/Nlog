# 什么是Currying(柯里化)

柯里化是一种函数的转换，它是指将一个函数从可调用的 `f(a, b, c)` 转换为可调用的 `f(a)(b)(c)`。

```js
//柯里化函数
function currying(f){
    return function(a){
        return function(b){
            return a+b;
        }
    }
}
currying(1)(2)//3

//普通函数
function common(a,b){
    return a+b
} 

 common(1,2)//3
```



1. 为了使整个程序无论如何都能正常工作，`sum` 的结果必须是函数。
2. 这个函数必须将两次调用之间的当前值保存在内存中。
3. 根据这个题目，当函数被用于 `==` 比较时必须转换成数字。函数是对象，所以转换规则会按照 [对象 — 原始值转换](https://zh.javascript.info/object-toprimitive) 章节所讲的进行，我们可以提供自己的方法来返回数字。

```js
function sum(a){
    let curentSum = a
    function f(b){
        curentSum += b
        return f
    }
    f.toString = function(){
        return currentSum;
    }
    return f
}
```

