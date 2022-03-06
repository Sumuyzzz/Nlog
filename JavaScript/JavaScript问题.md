https://github.com/lydiahallie/javascript-questions#13-what-are-the-three-phases-of-event-propagation



###### What are the three phases of event propagation?

- A: Target > Capturing > Bubbling
- B: Bubbling > Target > Capturing
- C: Target > Bubbling > Capturing
- D: Capturing > Target > Bubbling

#### Answer: D

During the **capturing** phase, the event goes through the ancestor elements down to the target element. It then reaches the **target** element, and **bubbling** begins.（在**捕获**（capturing）阶段中，事件从祖先元素向下传播到目标元素。当事件达到**目标**（target）元素后，**冒泡**（bubbling）才开始。）

[![img](https://camo.githubusercontent.com/5fd2d347d044150e4ae35091622f0628f0eb7893966f03c8955ca271f3153e47/68747470733a2f2f692e696d6775722e636f6d2f4e31386f5267642e706e67)](https://camo.githubusercontent.com/5fd2d347d044150e4ae35091622f0628f0eb7893966f03c8955ca271f3153e47/68747470733a2f2f692e696d6775722e636f6d2f4e31386f5267642e706e67)



***

###### What's the output?

```js
function getPersonInfo(one, two, three) {
  console.log(one);
  console.log(two);
  console.log(three);
}

const person = 'Lydia';
const age = 21;

getPersonInfo`${person} is ${age} years old`;
```

- A: `"Lydia"` `21` `["", " is ", " years old"]`
- B: `["", " is ", " years old"]` `"Lydia"` `21`
- C: `"Lydia"` `["", " is ", " years old"]` `21`

#### Answer: B

If you use tagged template literals, the value of the first argument is always an array of the string values. The remaining arguments get the values of the passed expressions!（如果使用标记模板字面量，第一个参数的值总是包含字符串的数组。其余的参数获取的是传递的表达式的值！）

****

###### 输出是什么？

```js
function getAge(...args) {
  console.log(typeof args)
}

getAge(21)
```



- A: `"number"`
- B: `"array"`
- C: `"object"`
- D: `"NaN"`

#### 答案: C

扩展运算符（`...args`）会返回实参组成的数组。而数组是对象，因此 `typeof args` 返回 `"object"`。

***

###### 输出是什么？

```js
const sum = eval('10*10+5')
```

- A: `105`
- B: `"105"`
- C: `TypeError`
- D: `"10*10+5"`

#### 答案: A

代码以字符串形式传递进来，`eval` 对其求值。如果它是一个表达式，就像本例中那样，它对表达式求值。表达式是 `10 * 10 + 5`。这将返回数字 `105`。

***

###### cool_secret 可访问多长时间？

```js
sessionStorage.setItem('cool_secret', 123)
```

- A: 永远，数据不会丢失。
- B: 当用户关掉标签页时。
- C: 当用户关掉整个浏览器，而不只是关掉标签页。
- D: 当用户关闭电脑时。

***

###### JavaScript 全局执行上下文为你做了两件事：全局对象和 this 关键字。

- A: 对
- B: 错
- C: 看情况

#### 答案: A

基本执行上下文是全局执行上下文：它是代码中随处可访问的内容。

***

```js
String.prototype.giveLydiaPizza = () => {
  return 'Just give Lydia pizza already!'
}

const name = 'Lydia'

name.giveLydiaPizza()
```



- A: `"Just give Lydia pizza already!"`
- B: `TypeError: not a function`
- C: `SyntaxError`
- D: `undefined`

#### 答案: A

`String` 是内置的构造函数，我们可以向它添加属性。我只是在它的原型中添加了一个方法。基本类型字符串被自动转换为字符串对象，由字符串原型函数生成。因此，所有 string(string 对象)都可以访问该方法！

***

###### . 输出是什么？

```js
const a = {}
const b = { key: 'b' }
const c = { key: 'c' }

a[b] = 123
a[c] = 456

console.log(a[b])
```

- A: `123`
- B: `456`
- C: `undefined`
- D: `ReferenceError`

#### 答案: B

对象的键被自动转换为字符串。我们试图将一个对象 `b` 设置为对象 `a` 的键，且相应的值为 `123`。

然而，当字符串化一个对象时，它会变成 `"[object Object]"`。因此这里说的是，`a["[object Object]"] = 123`。然后，我们再一次做了同样的事情，`c` 是另外一个对象，这里也有隐式字符串化，于是，`a["[object Object]"] = 456`。

然后，我们打印 `a[b]`，也就是 `a["[object Object]"]`。之前刚设置为 `456`，因此返回的是 `456`

***

###### 输出是什么？

```js
(() => {
  let x, y
  try {
    throw new Error()
  } catch (x) {
    (x = 1), (y = 2)
    console.log(x)
  }
  console.log(x)
  console.log(y)
})()
```

- A: `1` `undefined` `2`
- B: `undefined` `undefined` `undefined`
- C: `1` `1` `2`
- D: `1` `undefined` `undefined`

####  A

`catch` 代码块接收参数 `x`。当我们传递参数时，这与之前定义的变量 `x` 不同 。这个 `x` 是属于 `catch` 块级作用域的。

然后，我们将块级作用域中的变量赋值为 `1`，同时也设置了变量 `y` 的值。现在，我们打印块级作用域中的变量 `x`，值为 `1`。

`catch` 块之外的变量 `x` 的值仍为 `undefined`， `y` 的值为 `2`。当我们在 `catch` 块之外执行 `console.log(x)` 时，返回 `undefined`，`y` 返回 `2`。

***

###### 输出是什么？

```js
[[0, 1], [2, 3]].reduce(
  (acc, cur) => {
    return acc.concat(cur)
  },
  [1, 2]
)
```

- A: `[0, 1, 2, 3, 1, 2]`
- B: `[6, 1, 2]`
- C: `[1, 2, 0, 1, 2, 3]`
- D: `[1, 2, 6]`

#### 答案: C


[1, 2]`是初始值。初始值将会作为首次调用时第一个参数 `acc` 的值。在第一次执行时， `acc` 的值是 `[1, 2]`， `cur` 的值是 `[0, 1]`。合并它们，结果为 `[1, 2, 0, 1]`。 第二次执行， `acc` 的值是 `[1, 2, 0, 1]`， `cur` 的值是 `[2, 3]`。合并它们，最终结果为 `[1, 2, 0, 1, 2, 3]

***

######  输出是什么?

```js
function* generator(i) {
  yield i;
  yield i * 2;
}

const gen = generator(10);

console.log(gen.next().value);
console.log(gen.next().value);
```

- A: `[0, 10], [10, 20]`
- B: `20, 20`
- C: `10, 20`
- D: `0, 10 and 10, 20`

#### 答案: C

一般的函数在执行之后是不能中途停下的。但是，生成器函数却可以中途“停下”，之后可以再从停下的地方继续。当生成器遇到`yield`关键字的时候，会生成`yield`后面的值。注意，生成器在这种情况下不 *返回* (*return* )值，而是 *生成* (*yield*)值。

首先，我们用`10`作为参数`i`来初始化生成器函数。然后使用`next()`方法一步步执行生成器。第一次执行生成器的时候，`i`的值为`10`，遇到第一个`yield`关键字，它要生成`i`的值。此时，生成器“暂停”，生成了`10`。

然后，我们再执行`next()`方法。生成器会从刚才暂停的地方继续，这个时候`i`还是`10`。于是我们走到了第二个`yield`关键字处，这时候需要生成的值是`i*2`，`i`为`10`，那么此时生成的值便是`20`。所以这道题的最终结果是`10,20`。

***

###### 返回值是什么?

```js
const firstPromise = new Promise((res, rej) => {
  setTimeout(res, 500, "one");
});

const secondPromise = new Promise((res, rej) => {
  setTimeout(res, 100, "two");
});

Promise.race([firstPromise, secondPromise]).then(res => console.log(res));
```

- A: `"one"`
- B: `"two"`
- C: `"two" "one"`
- D: `"one" "two"`

#### 答案: B

当我们向`Promise.race`方法中传入多个`Promise`时，会进行 *优先* 解析。在这个例子中，我们用`setTimeout`给`firstPromise`和`secondPromise`分别设定了500ms和100ms的定时器。这意味着`secondPromise`会首先解析出字符串`two`。那么此时`res`参数即为`two`，是为输出结果。

***

######  输出是什么?

```js
const person = {
  name: "Lydia",
  age: 21
};

for (const item in person) {
  console.log(item);
}
```

- A: `{ name: "Lydia" }, { age: 21 }`
- B: `"name", "age"`
- C: `"Lydia", 21`
- D: `["name", "Lydia"], ["age", 21]`

#### 答案: B

在`for-in`循环中,我们可以通过对象的key来进行迭代,也就是这里的`name`和`age`。在底层，对象的key都是字符串（如果他们不是Symbol的话）。在每次循环中，我们将`item`设定为当前遍历到的key.所以一开始，`item`是`name`，之后 `item`输出的则是`age`。

***

######  `num`的值是什么?

```js
const num = parseInt("7*6", 10);
```

- A: `42`
- B: `"42"`
- C: `7`
- D: `NaN`

#### 答案: C

只返回了字符串中第一个字母. 设定了 *进制* 后 (也就是第二个参数，指定需要解析的数字是什么进制: 十进制、十六机制、八进制、二进制等等……),`parseInt` 检查字符串中的字符是否合法. 一旦遇到一个在指定进制中不合法的字符后，立即停止解析并且忽略后面所有的字符。

`*`就是不合法的数字字符。所以只解析到`"7"`，并将其解析为十进制的`7`. `num`的值即为`7`.

***

###### 输出的是什么?

```js
function getInfo(member, year) {
  member.name = "Lydia";
  year = "1998";
}

const person = { name: "Sarah" };
const birthYear = "1997";

getInfo(person, birthYear);

console.log(person, birthYear);
```

- A: `{ name: "Lydia" }, "1997"`
- B: `{ name: "Sarah" }, "1998"`
- C: `{ name: "Lydia" }, "1998"`
- D: `{ name: "Sarah" }, "1997"`

#### 答案: A

普通参数都是 *值* 传递的，而对象则不同，是 *引用* 传递。所以说，`birthYear`是值传递，因为他是个字符串而不是对象。当我们对参数进行值传递时，会创建一份该值的 *复制* 。（可以参考问题46）

变量`birthYear`有一个对`"1997"`的引用，而传入的参数也有一个对`"1997"`的引用，但二者的引用并不相同。当我们通过给 `year`赋值`"1998"`来更新`year`的值的时候我们只是更新了`year`（的引用）。此时`birthYear`仍然是`"1997"`.

而`person`是个对象。参数`member`引用与之 *相同的* 对象。当我们修改`member`所引用对象的属性时,`person`的相应属性也被修改了,因为他们引用了相同的对象. `person`的 `name`属性也变成了 `"Lydia"`.

***

###### 输出是什么?

```js
function greeting() {
  throw "Hello world!";
}

function sayHi() {
  try {
    const data = greeting();
    console.log("It worked!", data);
  } catch (e) {
    console.log("Oh no an error:", e);
  }
}

sayHi();
```

- A: `"It worked! Hello world!"`
- B: `"Oh no an error: undefined`
- C: `SyntaxError: can only throw Error objects`
- D: `"Oh no an error: Hello world!`

#### 答案: D

通过`throw`语句，我么可以创建自定义错误。 而通过它，我们可以抛出异常。异常可以是一个**字符串**, 一个 **数字**, 一个 **布尔类型** 或者是一个 **对象**。在本例中，我们的异常是字符串`'Hello world'`.

通过 `catch`语句，我们可以设定当`try`语句块中抛出异常后应该做什么处理。在本例中抛出的异常是字符串`'Hello world'`. `e`就是这个字符串，因此被输出。最终结果就是`'Oh an error: Hello world'`.

***

```js
(() => {
  let x = (y = 10);
})();

console.log(typeof x);
console.log(typeof y);
```

- A: `"undefined", "number"`
- B: `"number", "number"`
- C: `"object", "number"`
- D: `"number", "undefined"`

`let x = y = 10;` 是下面这个表达式的缩写:

```js
y = 10;
let x = y;
```

我们设定`y`等于`10`时,我们实际上增加了一个属性`y`给全局对象(浏览器里的`window`, Nodejs里的`global`)。在浏览器中， `window.y`等于`10`.

然后我们声明了变量`x`等于`y`,也是`10`.但变量是使用 `let`声明的，它只作用于 *块级作用域*, 仅在声明它的块中有效；就是案例中的立即调用表达式(IIFE)。使用`typeof`操作符时, 操作值 `x`没有被定义：因为我们在`x`声明块的外部，无法调用它。这就意味着`x`未定义。未分配或是未声明的变量类型为`"undefined"`. `console.log(typeof x)`返回`"undefined"`.

而我们创建了全局变量`y`，并且设定`y`等于`10`.这个值在我们的代码各处都访问的到。 `y`已经被定义了，而且有一个`"number"`类型的值。 `console.log(typeof y)`返回`"number"`.

***

```js
const name = "Lydia";
age = 21;

console.log(delete name); //false
console.log(delete age); //true


const name = "Lydia";
var age = 21;

console.log(delete name); //false
console.log(delete age); //false
```

- A: `false`, `true`
- B: `"Lydia"`, `21`
- C: `true`, `true`
- D: `undefined`, `undefined`

`delete`操作符返回一个布尔值： `true`指删除成功，否则返回`false`. 但是通过 `var`, `const` 或 `let` 关键字声明的变量无法用 `delete` 操作符来删除。

`name`变量由`const`关键字声明，所以删除不成功:返回 `false`. 而我们设定`age`等于`21`时,我们实际上添加了一个名为`age`的属性给全局对象。对象中的属性是可以删除的，全局对象也是如此，所以`delete age`返回`true`.

***

###### 63. What's the output?

```js
let num = 10;

const increaseNumber = () => num++; //先输出num的值在自增，num的值是11
const increasePassedNumber = number => number++; //同理

const num1 = increaseNumber(); //所以这里是10
const num2 = increasePassedNumber(num1); //同理

console.log(num1);
console.log(num2);
```

- **A: `10`, `10`**
- B: `10`, `11`
- C: `11`, `11`
- D: `11`, `12`

***

###### 73. What's the output?

```js
async function getData() {
  return await Promise.resolve('I made it!');
}

const data = getData();
console.log(data);
```

- A: `"I made it!"`
- B: `Promise {<resolved>: "I made it!"}`
- C: `Promise {<pending>}`
- D: `undefined`

#### Answer: C

An async function always returns a promise. The `await` still has to wait for the promise to resolve: a pending promise gets returned when we call `getData()` in order to set `data` equal to it.

If we wanted to get access to the resolved value `"I made it"`, we could have used the `.then()` method on `data`:`data.then(res => console.log(res))`


This would've logged `"I made it!"`

###### 85. What kind of information would get logged?

```js
fetch('https://www.website.com/api/user/1')
  .then(res => res.json())
  .then(res => console.log(res));
```

- A: The result of the `fetch` method.
- B: The result of the second invocation of the `fetch` method.
- C: The result of the callback in the previous `.then()`.
- D: It would always be undefined.

#### Answer: C

The value of `res` in the second `.then` is equal to the returned value of the previous `.then`. You can keep chaining `.then`s like this, where the value is passed to the next handler.（ 第二个.then中res的值等于前一个.then的返回值。您可以像这样继续链接 .thens，将值传递给下一个处理程序。）

```js
console.log('I want pizza'[0]);
```

- A: `"""`
- B: `"I"`
- C: `SyntaxError`
- D: `undefined`

In order to get an character on a specific index in a string, you can use bracket notation. The first character in the string has index 0, and so on. In this case we want to get the element which index is 0, the character `"I'`, which gets logged.

Note that this method is not supported in IE7 and below. In that case, use `.charAt()`

```js
// module.js
export default () => 'Hello world';
export const name = 'Lydia';

// index.js
import * as data from './module';

console.log(data);
```

- A: `{ default: function default(), name: "Lydia" }`
- B: `{ default: function default() }`
- C: `{ default: "Hello world", name: "Lydia" }`
- D: Global object of `module.js`

#### Answer: A

With the `import * as name` syntax, we import *all exports* from the `module.js` file into the `index.js` file as a new object called `data` is created. In the `module.js` file, there are two exports: the default export, and a named export. The default export is a function which returns the string `"Hello World"`, and the named export is a variable called `name` which has the value of the string `"Lydia"`.

The `data` object has a `default` property for the default export, other properties have the names of the named exports and their corresponding values.

***

```js
function getItems(fruitList, ...args, favoriteFruit) {
  return [...fruitList, ...args, favoriteFruit]
}

getItems(["banana", "apple"], "pear", "orange")
```

- A: `["banana", "apple", "pear", "orange"]`
- B: `[["banana", "apple"], "pear", "orange"]`
- C: `["banana", "apple", ["pear"], "orange"]`
- D: `SyntaxError`

#### Answer: D

`...args` is a rest parameter. The rest parameter's value is an array containing all remaining arguments, **and can only be the last parameter**! In this example, the rest parameter was the second parameter. This is not possible, and will throw a syntax error.

```js
function getItems(fruitList, favoriteFruit, ...args) {
  return [...fruitList, ...args, favoriteFruit];
}

getItems(['banana', 'apple'], 'pear', 'orange');
```

The above example works. This returns the array `[ 'banana', 'apple', 'orange', 'pear' ]`

***

```js
const info = {
  [Symbol('a')]: 'b'
}

console.log(info)
console.log(Object.keys(info))
```

- A: `{Symbol('a'): 'b'}` and `["{Symbol('a')"]`
- B: `{}` and `[]`
- C: `{ a: "b" }` and `["a"]`
- D: `{Symbol('a'): 'b'}` and `[]`

`Symbol`类型是不可枚举的。`Object.keys`方法返回对象上的所有可枚举的键属性。`Symbol`类型是不可见的，并返回一个空数组。 记录整个对象时，所有属性都是可见的，甚至是不可枚举的属性。

这是`Symbol`的众多特性之一：除了表示完全唯一的值（防止对象意外名称冲突，例如当使用2个想要向同一对象添加属性的库时），您还可以`隐藏`这种方式对象的属性（尽管不完全。你仍然可以使用`Object.getOwnPropertySymbols()`方法访问 `Symbol`。

***

```js
const getList = ([x, ...y]) => [x, y]
const getUser = user => { name: user.name, age: user.age }

const list = [1, 2, 3, 4]
const user = { name: "Lydia", age: 21 }

console.log(getList(list))
console.log(getUser(user))
```

- A: `[1, [2, 3, 4]]` and `undefined`
- B: `[1, [2, 3, 4]]` and `{ name: "Lydia", age: 21 }`
- C: `[1, 2, 3, 4]` and `{ name: "Lydia", age: 21 }`
- D: `Error` and `{ name: "Lydia", age: 21 }`

#### 答案: A

`getList`函数接收一个数组作为其参数。 在`getList`函数的括号之间，我们立即解构这个数组。 您可以将其视为：

```js
[x, ...y] = [1, 2, 3, 4]
```

使用剩余的参数`... y`，我们将所有剩余参数放在一个数组中。 在这种情况下，其余的参数是`2`，`3`和`4`。 `y`的值是一个数组，包含所有其余参数。 在这种情况下，`x`的值等于`1`，所以当我们打印`[x，y]`时，会打印`[1，[2,3,4]]`。

`getUser`函数接收一个对象。对于箭头函数，如果只返回一个值，我们不必编写花括号。但是，如果您想从一个箭头函数返回一个对象，您必须在圆括号之间编写它，否则不会返回任何值!下面的函数将返回一个对象:

```js
const getUser = user => ({ name: user.name, age: user.age })
```

由于在这种情况下不返回任何值，因此该函数返回`undefined`。

***

```js
const myPromise = () => Promise.resolve('I have resolved!')

function firstFunction() {
  myPromise().then(res => console.log(res))
  console.log('second')
}

async function secondFunction() {
  console.log(await myPromise())
  console.log('second')
}

firstFunction()
secondFunction()
```

- A: `I have resolved!`, `second` and `I have resolved!`, `second`
- B: `second`, `I have resolved!` and `second`, `I have resolved!`
- C: `I have resolved!`, `second` and `second`, `I have resolved!`
- D: `second`, `I have resolved!` and `I have resolved!`, `second`

#### 答案: D

有了promise，我们通常会说：当我想要调用某个方法，但是由于它可能需要一段时间，因此暂时将它放在一边。只有当某个值被resolved/rejected，并且执行栈为空时才使用这个值。

我们可以在`async`函数中通过`.then`和`await`关键字获得该值。 尽管我们可以通过`.then`和`await`获得promise的价值，但是它们的工作方式有所不同。

在 `firstFunction`中，当运行到`myPromise`方法时我们将其放在一边，即promise进入微任务队列，其他后面的代码（`console.log('second')`）照常运行，因此`second`被打印出，`firstFunction`方法到此执行完毕，执行栈中宏任务队列被清空，此时开始执行微任务队列中的任务，`I have resolved`被打印出。

在`secondFunction`方法中，我们通过`await`关键字，暂停了后面代码的执行，直到异步函数的值被解析才开始后面代码的执行。这意味着，它会等着直到 `myPromise` 以值`I have resolved`被解决之后，下一行`second`才开始执行。

***

```js
const colorConfig = {
  red: true,
  blue: false,
  green: true,
  black: true,
  yellow: false,
}

const colors = ["pink", "red", "blue"]

console.log(colorConfig.colors[1])
```

- A: `true`
- B: `false`
- C: `undefined`
- D: `TypeError`

#### 答案: D

在JavaScript中，我们有两种访问对象属性的方法：括号表示法或点表示法。 在此示例中，我们使用点表示法（`colorConfig.colors`）代替括号表示法（`colorConfig [“ colors”]`）。

使用点表示法，JavaScript会尝试使用该确切名称在对象上查找属性。 在此示例中，JavaScript尝试在colorconfig对象上找到名为colors的属性。 没有名为“colors”的属性，因此返回“undefined”。 然后，我们尝试使用`[1]`访问第一个元素的值。 我们无法对未定义的值执行此操作，因此会抛出`Cannot read property '1' of undefined`。

JavaScript解释（或取消装箱）语句。 当我们使用方括号表示法时，它会看到第一个左方括号`[`并一直进行下去，直到找到右方括号`]`。 只有这样，它才会评估该语句。 如果我们使用了colorConfig [colors [1]]，它将返回colorConfig对象上red属性的值。

***

```js
function* generatorOne() {
  yield ['a', 'b', 'c'];
}

function* generatorTwo() {
  yield* ['a', 'b', 'c'];
}

const one = generatorOne()
const two = generatorTwo()

console.log(one.next().value)
console.log(two.next().value)
```

- A: `a` and `a`
- B: `a` and `undefined`
- C: `['a', 'b', 'c']` and `a`
- D: `a` and `['a', 'b', 'c']`

#### 答案: C

通过 `yield` 关键字, 我们在 `Generator` 函数里执行`yield`表达式. 通过 `yield*` 关键字, 我们可以在一个`Generator` 函数里面执行（`yield`表达式）另一个 `Generator` 函数, 或可遍历的对象 (如数组).

在函数 `generatorOne` 中, 我们通过 `yield` 关键字 yield 了一个完整的数组 `['a', 'b', 'c']`。函数`one`通过`next`方法返回的对象的`value` 属性的值 (`one.next().value`) 等价于数组 `['a', 'b', 'c']`.

```js
console.log(one.next().value) // ['a', 'b', 'c']
console.log(one.next().value) // undefined
```

在函数 `generatorTwo` 中, 我们使用 `yield*` 关键字。就相当于函数`two`第一个`yield`的值, 等价于在迭代器中第一个 `yield` 的值。数组`['a', 'b', 'c']`就是这个迭代器. 第一个 `yield` 的值就是 `a`, 所以我们第一次调用 `two.next().value`时, 就返回`a`。

```js
console.log(two.next().value) // 'a'
console.log(two.next().value) // 'b'
console.log(two.next().value) // 'c'
console.log(two.next().value) // undefined
```

***

124. 输出什么？

```js
async function* range(start, end) {
	for (let i = start; i <= end; i++) {
		yield Promise.resolve(i);
	}
}

(async () => {
	const gen = range(1, 3);
	for await (const item of gen) {
		console.log(item);
	}
})();
```



- A: `Promise {1}` `Promise {2}` `Promise {3}`
- B: `Promise {<pending>}` `Promise {<pending>}` `Promise {<pending>}`
- C: `1` `2` `3`
- D: `undefined` `undefined` `undefined`

#### 答案: C

我们给 函数range 传递： `Promise{1}`, `Promise{2}`, `Promise{3}`，Generator 函数 `range` 返回一个全是 async object promise 数组。我们将 async object 赋值给变量 `gen`，之后我们使用`for await ... of` 进行循环遍历。我们将返回的 Promise 实例赋值给 `item`： 第一个返回 `Promise{1}`， 第二个返回 `Promise{2}`，之后是 `Promise{3}`。因为我们正 *awaiting* `item` 的值，resolved 状态的 promsie，promise数组的resolved *值* 以此为： `1`，`2`，`3`.

***

```js
function getFine(speed, amount) {
  const formattedSpeed = new Intl.NumberFormat({
    'en-US',
    { style: 'unit', unit: 'mile-per-hour' }
  }).format(speed)

  const formattedAmount = new Intl.NumberFormat({
    'en-US',
    { style: 'currency', currency: 'USD' }
  }).format(amount)

  return `The driver drove ${formattedSpeed} and has to pay ${formattedAmount}`
}

console.log(getFine(130, 300))
```

- A: The driver drove 130 and has to pay 300
- B: The driver drove 130 mph and has to pay $300.00
- C: The driver drove undefined and has to pay undefined
- D: The driver drove 130.00 and has to pay 300.00

#### 答案: B

通过方法 `Intl.NumberFormat`，我们可以格式化任意区域的数字值。我们对数字值 `130` 进行 `mile-per-hour` 作为 `unit` 的 `en-US` 区域 格式化，结果为 `130 mph`。对数字值 `300` 进行 `USD` 作为 `currentcy` 的 `en-US` 区域格式化，结果为 `$300.00`.

***

```js
const name = "Lydia Hallie";
const age = 21;

console.log(Number.isNaN(name));
console.log(Number.isNaN(age));

console.log(isNaN(name));
console.log(isNaN(age));
```

- A: `true` `false` `true` `false`
- B: `true` `false` `false` `false`
- C: `false` `false` `true` `false`
- D: `false` `true` `false` `true`

#### 答案: C

通过方法 `Number.isNaN`，你可以检测你传递的值是否为 *数字值* 并且是否等价于 `NaN`。`name` 不是一个数字值，因此 `Number.isNaN(name)` 返回 `false`。`age` 是一个数字值，但它不等价于 `NaN`，因此 `Number.isNaN(age)` 返回 `false`.

通过方法 `isNaN`， 你可以检测你传递的值是否一个 number。`name` 不是一个 `number`，因此 `isNaN(name)` 返回 `true`. `age` 是一个 `number` 因此 `isNaN(age)` 返回 `false`.

***

###### 134. 我们怎样才能在 `index.js` 中调用 `sum.js?` 中的 `sum`？

```js
// sum.js
export default function sum(x) {
	return x + x;
}

// index.js
import * as sum from "./sum";
```

- A: `sum(4)`
- B: `sum.sum(4)`
- C: `sum.default(4)`
- D: 默认导出不用 `*` 来导入，只能具名导出

#### 答案: C

使用符号 `*`，我们引入文件中的所有值，包括默认和具名。如果我们有以下文件：

```js
// info.js
export const name = "Lydia";
export const age = 21;
export default "I love JavaScript";

// index.js
import * as info from "./info";
console.log(info);
```

将会输出以下内容：

```js
{
  default: "I love JavaScript",
  name: "Lydia",
  age: 21
}
```

以 `sum` 为例，相当于以下形式引入值 `sum`：

```
{ default: function sum(x) { return x + x } }
```

我们可以通过调用 `sum.default` 来调用该函数























## 网上的问题

**1. 判断输出结果，并且解释原因？**

```js
var a = 1;        
(function a () {            
    a = 2;            
    console.log(a);        
})();
// 输出结果
ƒ a () {
           a = 2;
           console.log(a);
       }复制代码
```



这道题，猛地一看，很多人都会觉得，console.log(a) 的值为 2，其实不然，

立即调用的函数表达式（IIFE） 有一个 自己独立的 作用域，如果函数名称与内部变量名称冲突，就会永远执行函数本身；所以上面的结果输出是函数本身；







