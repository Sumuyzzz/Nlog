# 对比构建版本

| UMD                           | CommonJS           | ES Module (基于构建工具使用) | ES Module (直接用于浏览器) |                        |
| :---------------------------- | :----------------- | :--------------------------- | :------------------------- | ---------------------- |
| **完整版**                    | vue.js             | vue.common.js                | vue.esm.js                 | vue.esm.browser.js     |
| **只包含运行时版**            | vue.runtime.js     | vue.runtime.common.js        | vue.runtime.esm.js         | -                      |
| **完整版 (生产环境)**         | vue.min.js         | -                            | -                          | vue.esm.browser.min.js |
| **只包含运行时版 (生产环境)** | vue.runtime.min.js | -                            | -                          | -                      |



# template 和 render 怎么用

## 1.完整版直接使用`template`（可以直接写HTML）

- 基本写法

```
new Vue({
  template: '<div>{{ n }}</div>'
})
```

- 添加+1按钮

```js
new Vue({
  el:'#app',
  template:`<div>
    {{n}}
    <button @click="add">+1</button>
    </div>`,
  data:{
    n:0
  },
  methods:{
    add(){
      this.n += 1
    }
  }
})
```

## 2.非完整版（`render(){}`）

- 基本写法

```
new Vue({
  render (h) {
    return h('div', this.n)
  }
})
```

- 添加+1按钮

```js
new Vue({
  el: '#app',
  render(h) {
    return h('div', [this.n, h('button', {on: {click: this.add}}, '+1')])
  },
  data: {
    n: 0
  },
  methods: {
    add() {
      this.n += 1
    }
  }
})
```