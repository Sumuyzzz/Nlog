### 算术运算符

>```javascript
>true + true //2
>false + false //0
>```
>
>布尔值都会自动转成数值，然后再相加。所以`true + true` 得到2，`false + false `得到0。

>```javascript
>'a'+'b'+'cd'//"abcd"
>```
>
>如果是多个字符串相加，则加法运算符变成连接运算符，返回一串新的字符串。

> ```javascript
> 1+'a'// '1a'
> false + 'a'//'false'
> ```
>

> **注意：当字符串和非字符串相加时，会导致”重载“现象，可能执行两种运算**
>
> ```javascript
> 'a'+1+2//"a12"
> 1+2+'a'//"3a"
> ```
>
> 除了加法其他运算符都不会发生重载，它们的规则是：所有运算子一律转为数值，再进行相应的数学运算。
>

>
> ### 对象的相加   
>
> 如果运算子是对象，必须先转成原始类型的值，然后再相加。
>
> ```
> var obj = { p: 1 };
> obj + 2 // "[object Object]2"
> ```
>
> 上面代码中，对象`obj`转成原始类型的值是`[object Object]`，再加`2`就得到了上面的结果。
>
> 对象转成原始类型的值，规则如下。
>
> 首先，自动调用对象的`valueOf`方法。
>
> ```
> var obj = { p: 1 };
> obj.valueOf() // { p: 1 }
> ```
>
> 一般来说，对象的`valueOf`方法总是返回对象自身，这时再自动调用对象的`toString`方法，将其转为字符串。
>
> ```
> var obj = { p: 1 };
> obj.valueOf().toString() // "[object Object]"
> ```
>
> 对象的`toString`方法默认返回`[object Object]`，所以就得到了最前面那个例子的结果。
>
> 知道了这个规则以后，就可以自己定义`valueOf`方法或`toString`方法，得到想要的结果。
>
> ```
> var obj = {
>   valueOf: function () {
>     return 1;
>   }
> };
> 
> obj + 2 // 3
> ```
>
> 上面代码中，我们定义`obj`对象的`valueOf`方法返回`1`，于是`obj + 2`就得到了`3`。这个例子中，由于`valueOf`方法直接返回一个原始类型的值，所以不再调用`toString`方法。
>
> 下面是自定义`toString`方法的例子。
>
> ```
> var obj = {
>   toString: function () {
>     return 'hello';
>   }
> };
> 
> obj + 2 // "hello2"
> ```
>
> 上面代码中，对象`obj`的`toString`方法返回字符串`hello`。前面说过，只要有一个运算子是字符串，加法运算符就变成连接运算符，返回连接后的字符串。
>
> 这里有一个特例，如果运算子是一个`Date`对象的实例，那么会优先执行`toString`方法。
>
> ```
> var obj = new Date();
> obj.valueOf = function () { return 1 };
> obj.toString = function () { return 'hello' };
> 
> obj + 2 // "hello2"
> ```
>
> 上面代码中，对象`obj`是一个`Date`对象的实例，并且自定义了`valueOf`方法和`toString`方法，结果`toString`方法优先执行。



