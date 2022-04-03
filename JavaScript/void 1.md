

### JavaScript中的void

JS中的void是一个运算符，它对紧跟其后的表达式求值。不管是什么表达式，void总是返回undefined。



void是一种调用立即执行函数的不错的方式。

```js
void function() {
   console.log('What')
}()
```

根据这个可以得出，可以避免污染全局命名空间：

```js
void function aRecursion(i) {
   if(i > 0) {
       console.log(i--)
       aRecursion(i)
   }
}(3)

console.log(typeof aRecursion) // undefined
```

