## Iterator（遍历器）的概念
定义：一种接口，为不同数据机构统一的访问机制，只要部署了接口，对象就可以实现遍历操作。
作用：
1. 为数据接口提供一种统一的访问接口
2. 使成员能够按某种次序排列
3. 给`for...of`提供服务

原生具备 Iterator 接口的数据结构如下。

-   Array
-   Map
-   Set
-   String
-   TypedArray
-   函数的 arguments 对象
-   NodeList 对象


## 默认 Iterator 接口
es6规定，只要在数据结构内部设置，`Symbol.iterator`属性，就认为是`iterable`.

例如
```js
const obj = {
  [Symbol.iterator] : function () {
    return {
      next: function () {
        return {
          value: 1,
          done: true
        };
      }
    };
  }
};
```
当使用`for...of`时，会自动执行这个`Symbol.iterator`方法，自动返回一个next方法，里面包含属性的value值的对象。


之所以对象没有部署Iterator 接口，是因为对象遍历顺序不确定。



