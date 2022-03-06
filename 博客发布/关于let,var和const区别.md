## var

* 变量提升
* 全局作用域和函数作用域





### 变量提升

```js
function foo() { 
 console.log(age); 
 var age = 26; 
} 
foo(); // undefined 

```

等价于下面的表达

```js
function foo() { 
 var age; 
 console.log(age); 
 age = 26; 
} 
foo(); // undefined 
```





### 全局和函数

使用 var 操作符定义的变量会成为包含它的函数的局部变量。

但是不用var操作符定义的变量会默认为全局变量

```js
function test() { 
 var message = "hi"; // 局部变量
} 
test(); 
console.log(message); // 出错！
```

```js
function test() { 
 message = "hi"; // 全局变量
} 
test(); 
console.log(message); // "hi" 
```







## let

* 暂时性死区
* 不能重复声明
* 全局作用域和函数作用域,块级作用域



### 暂时性死区

```js
// name 会被提升
console.log(name); // undefined 
var name = 'Matt'; 
// age 不会被提升
console.log(age); // ReferenceError：age 没有定义
let age = 26; 
```

只有在声明之后的变量才能使用



### 不能重复声明

```js
let name='小东'
let name = '小西'
// Identifier 'name' has already been declared
```



### 作用域

```js
let name ='小明'
function fn(){
    let name = '小丑'
    {let name = '小美'}
}

```



### for循环带来的问题





const

* 声明之后立即赋值
* 无法修改基本类型



声明