创建路由时的一个配置，也就是history配置。

## hash
这里的hash指的是 **#模式**。


### 文档描述
>它在内部传递的实际 URL 之前使用了一个哈希字符（`#`）。由于这部分 URL 从未被发送到服务器，所以它不需要在服务器层面上进行任何特殊处理。不过，**它在 SEO 中确实有不好的影响**。



### 创建方式
```js
import { createRouter, createWebHistory } from 'vue-router'

const router = createRouter({
  history: createWebHistory(),
  routes: [
    //...
  ],
})
```

也就是不需要借助服务器


## html5


