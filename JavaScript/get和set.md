写法一
```js
var obj = Object.defineProperty({}, 'p', {
  get: function () {
    return 'getter';
  },
  set: function (value) {
    console.log('setter: ' + value);
  }
});

obj.p // "getter"
obj.p = 123 // "setter: 123"
```
一旦对目标属性定义了存取器，那么存取的时候，都将执行对应的函数。


写法二
```js
var obj = {
  get p() {
    return 'getter';
  },
  set p(value) {
    console.log('setter: ' + value);
  }
};
```
差异：
第一种写法，属性`p`的`configurable`和`enumerable`都为`false`，从而导致属性`p`是不可遍历的；第二种写法，属性`p`的`configurable`和`enumerable`都为`true`，因此属性`p`是可遍历的。实际开发中，写法二更常用。
