# Math.abs
>返回指定数字绝对值

```js
Math.abs('-1');     // 1
Math.abs(-2);       // 2
Math.abs(null);     // 0
Math.abs('');       // 0
Math.abs([]);       // 0
Math.abs([2]);      // 2
Math.abs([1,2]);    // NaN
Math.abs({});       // NaN
Math.abs('string'); // NaN
Math.abs();         // NaN
```


# Math.PI
>圆的周长与直径的比例

```js
function calculateCircumference (radius) {
  return 2 * Math.PI * radius;
}
```

# Math.ceil()
>四舍五入之五入 ，向大取整

```js
Math.ceil(.95) //1

Math.ceil(3.004) //4

```

# Math.floor()
>四舍五入之四舍，向小取整

```js
Math.floor(45.95) //45

Math.floor(-45.05) //-46

```
# Math.max()
>返回一组数中的最大值。



```js
Math.max(1, 3, 2) //3

const array1 = [-1, -3, -2];

Math.max(...array1) //-1
```

# Math.min()
>零个或更多个数值的最小值

```js
Math.min(1, 3, 2) //1

const array1 = [-1, -3, -2];

Math.min(...array1) //-3
```

# Math.random()
> 返回一个0~1的随机数
```js
function getRandomInt(max) {
  return Math.ceil(Math.random() * max);
}
console.log(getRandomInt(3)); // 1 or 2 ,3


console.log(getRandomInt(1)); //0,1
```
# Math.round()
>返回一个数字四舍五入后最接近的整数

```js

Math.round(20.49); //20


Math.round(-20.5);   //-20
```





# 参考
[Math](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Math)