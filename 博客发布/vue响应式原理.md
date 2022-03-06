### 前言

Vue 最独特的特性之一，是其非侵入性的响应式系统。数据模型仅仅是普通的 JavaScript 对象。而当你修改它们时，视图会进行更新。这使得状态管理非常简单直接，不过理解其工作原理同样重要，这样你可以避开一些常见的问题。—-官方文档



## 什么是响应式

我们先来看个例子：

```html
<div id="app">
    <div>Price :￥{{ price }}</div>
    <div>Total:￥{{ price * quantity }}</div>
    <div>Taxes: ￥{{ totalPriceWithTax }}</div>
    <button @click="changePrice">改变价格</button>
</div>
var app = new Vue({
  el: '#app',
  data() {
    return {
      price: 5.0,
      quantity: 2
    };
  },
  computed: {
    totalPriceWithTax() {
      return this.price * this.quantity * 1.03;
    }
  },
  methods: {
    changePrice() {
      this.price = 10;
    }
  }
})
```

[![img](https://image.fundebug.com/2019-07-10-01.gif)](https://image.fundebug.com/2019-07-10-01.gif)

上例中当price 发生变化的时候，Vue就知道自己需要做三件事情：

- 更新页面上price的值
- 计算表达式 price*quantity 的值，更新页面
- 调用totalPriceWithTax 函数，更新页面

数据发生变化后，会重新对页面渲染，这就是Vue响应式