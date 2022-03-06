Getter相当于computed计算属性



### 缘由：有时候需要通过state状态数据，过滤计算得到新的数据

```jS
computed: {
  doneTodosCount () {
    return this.$store.state.todos.filter(todo => todo.done).length
  }
}
```

觉得应该在vuex里面解决这个问题，所以就出现了getter这个功能，和计算属性一样，getter的返回值会根据原始的依赖值缓存所计算的值，当依赖值发生改变时才会重新计算。



### 使用方法

```js
const store = new Vuex.Store({
  state: {
    todos: [
      { id: 1, text: '...', done: true },
      { id: 2, text: '...', done: false }
    ]
  },
  getters: {
    doneTodos: state => {
      return state.todos.filter(todo => todo.done)
    }
  }
})
```



1. Getter会暴露一个对象，可通过`this.$store.getters`来访问

   ```js
   this.$store.getters.doneTodos // -> [{ id: 1, text: '...', done: true }]
   ```

2. 可作为第二参数传入

   ```js
   getters: {
     // ...
     doneTodosCount: (state, getters) => {
       return getters.doneTodos.length
     }
   }
   
   this.$store.getters.doneTodosCount // -> 1
   ```
   
3. 通过方法调用的方式，传入参数可以获取对象里面的数据

   ```js
   this.$store.getters.getTodoById(2) // -> { id: 2, text: '...', done: false }





## `mapGetters` 辅助函数

`mapGetters` 辅助函数仅仅是将 store 中的 getter 映射到局部计算属性：

```js
import { mapGetters } from 'vuex'

export default {
  // ...
  computed: {
  // 使用对象展开运算符将 getter 混入 computed 对象中
    ...mapGetters([
      'doneTodosCount',
      'anotherGetter',
      // ...
    ])
  }
}
```

如果你想将一个 getter 属性另取一个名字，使用对象形式：

```js
...mapGetters({
  // 把 `this.doneCount` 映射为 `this.$store.getters.doneTodosCount`
  doneCount: 'doneTodosCount'
})
```







