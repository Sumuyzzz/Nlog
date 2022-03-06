##  单一状态树

相当于实例的data

> 用一个对象就包含了全部的应用层级状态。至此它便作为一个“唯一数据源 ([SSOT (opens new window)](https://en.wikipedia.org/wiki/Single_source_of_truth))”而存在。
>
> 单一状态树让我们能够直接地定位任一特定的状态片段，**在调试的过程中也能轻易地取得整个当前应用状态的快照**。



## 在 Vue 组件中获得 Vuex 状态

使用计算属性的方法来获取Vuex的状态：



```js
//  这里就得需要导入  import store form vuex

const Counter = {
  template: `<div>{{ count }}</div>`,
  computed: {
    count () {
      return store.state.count //这里如果不需要this.$store
    }
  }
}
```





为了减少代码量和减少频繁导入次数，通过跟组件注册stroe,可以使用this.$store访问数据

```js

const app = new Vue({
  el: '#app',
  // 把 store 对象提供给 “store” 选项，这可以把 store 的实例注入所有的子组件
  store,
  components: { Counter },
  template: `
    <div class="app">
      <counter></counter>
    </div>
  `
})
```



```js
const Counter = {
  template: `<div>{{ count }}</div>`,
  computed: {
    count () {
      return this.$store.state.count
    }
  }
}
```







https://zhuanlan.zhihu.com/p/100941659



