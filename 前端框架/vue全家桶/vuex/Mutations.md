## 使用

**更改 Vuex 的 store 中的状态的唯一方法是提交 mutation。**

参数：

1. **事件类型 (type)**：应该叫做事件的名字，就是需要调用的方法名
2. **回调函数 (handler)**：

```js
const store = new Vuex.Store({
  state: {
    count: 1
  },
  mutations: {
    increment (state) {
      // 变更状态
      state.count++
    }
  }
})//这里定义了方法

//在使用的时候用store.commit的方式传进来执行
store.commit('increment',payload)

```

## 提交载荷（Payload）

开始传入额外参数

```js
mutations: {
  increment (state, n) {
    state.count += n
  }
}

//在另外的组件执行
store.commit('increment', 10)
```

在大多数情况下，载荷应该是一个对象，下面的写法实现和上面一样的

```js
mutations: {
  increment (state, payload) {
    state.count += payload.xxx
  }
}


store.commit('increment', {
    xxx:10
})
```

