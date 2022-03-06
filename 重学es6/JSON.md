JSON字符转化

JavaScript 提供了如下方法：

- `JSON.stringify` 将对象转换为 JSON。(stringify意思就是字符化,ify就是什么什么化,[simplify](https://dictionary.cambridge.org/zhs/词典/英语-汉语-简体/simplify)简单化[beautify](https://dictionary.cambridge.org/zhs/词典/英语-汉语-简体/beautify)美化)
- `JSON.parse` 将 JSON 转换回对象。

请注意，**JSON 编码的对象**与**对象字面量**有几个重要的区别：

- 字符串使用双引号。JSON 中没有单引号或反引号。所以 `'John'` 被转换为 `"John"`。
- 对象属性名称也是双引号的。这是强制性的。所以 `age:30` 被转换成 `"age":30`。

总的来说:**在JSON存储的对象,只认双引号**

JSON 支持以下数据类型：

- Objects `{ ... }`

- Arrays `[ ... ]`

- Primitives：

  - strings，
  - numbers，
  - boolean values `true/false`，
  - `null`。

  JSON 是语言无关的纯数据规范，因此一些特定于 JavaScript 的对象属性会被 `JSON.stringify` 跳过。

  即：

  - 函数属性（方法）。
  - Symbol 类型的属性。
  - 存储 `undefined` 的属性。

  ```javascript
  let user = {
    sayHi() { // 被忽略
      alert("Hello");
    },
    [Symbol("id")]: 123, // 被忽略
    something: undefined // 被忽略
  };
  
  alert( JSON.stringify(user) ); // {}（空对象）
  ```

