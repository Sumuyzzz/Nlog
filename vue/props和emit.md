## 介绍

`prop`翻译过来意思是道具，在`vue`里我的理解是实例组件上的功能，



用于子组件接收父组件数据的传递

## 使用

官网上的介绍：

> 早些时候，我们提到了创建一个博文组件的事情。问题是如果你不能向这个组件传递某一篇博文的标题或内容之类的我们想展示的数据的话，它是没有办法使用的。这也正是 prop 的由来。

> Prop 是你可以在组件上注册的一些自定义 attribute。

```vue
<template>
<div id="blog-post-demo" class="demo">
  <blog-post title="My journey with Vue"></blog-post>
  <blog-post title="Blogging with Vue"></blog-post>
  <blog-post title="Why Vue is so fun"></blog-post>
</div>
</template>
<script>
const app = Vue.createApp({})

app.component('blog-post', {
  props: ['title'],
  template: `<h4>{{ title }}</h4>`
})

app.mount('#blog-post-demo')
</script>
```

![image-20211129140347212](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20211129140347212.png)





高级点的用法

```vue
<template>
<div id="blog-posts-demo">
  <blog-post
    v-for="post in posts"
    :key="post.id"
    :title="post.title"
  ></blog-post>
</div>
</template>
<script>
const App = {
  data() {
    return {
      posts: [
        { id: 1, title: 'My journey with Vue' },
        { id: 2, title: 'Blogging with Vue' },
        { id: 3, title: 'Why Vue is so fun' }
      ]
    }
  }
}

const app = Vue.createApp(App)

app.component('blog-post', {
  props: ['title'],
  template: `<h4>{{ title }}</h4>`
})

app.mount('#blog-posts-demo')
</script>
```



## emit

翻译过来就是发射的意思

用于父组件接收子组件信息跟`props`类似







参考：[Vue通过$emit实现父子组件的通讯原理](https://www.codeleading.com/article/81795803628/)
