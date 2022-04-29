特点：

* 7大原始值之一，拥有唯一性和不可变性
* 不会发生对象属性命名冲突
* **一个symbol值能作为对象属性的标识符；这是该数据类型仅有的目的**
* 用作属性时，不可枚举

## 基本用法

使用`Symbol()`初始化

```js
let sym = Symbol()
console.log(typeof sym); // symbol 
```

也可以传入**字符串**参数作为**符号的描述**，，该描述并不能用来访问对应属性， 但它能用于**调试**

```js
let firstName = Symbol("first name");
let person = {};
person[firstName] = "Nicholas";
console.log("first name" in person); // false
console.log(person[firstName]); // "Nicholas"
console.log(firstName); // "Symbol(first name)"
```

> 符号没有字面量语法，这也是它们发挥作用的关键



### 对象字面量中的Symbol

如果我们要在对象字面量 `{...}` 中使用 Symbol，则需要使用方括号把它括起来

```jS
let id = Symbol("id");

let faker = {
  name: "faker",
  [id]:id //本质来讲不可枚举，所以无法访问
  //[id]相当于[Symbol("id")]
};
let joker = {
  name: "joker",
  [`id`]:id //通过变量获取
};
console.log(faker.id)//undefined

console.log(joker.id)//Symbol(id)

```



### Symbol 在 for…in 中会被跳过

Symbol 属性不参与 `for..in` 循环。

```js
let id = Symbol("id");
let user = {
  name: "John",
  age: 30,
  [id]: 123
};

for (let key in user){
    console.log(key)
}
```











