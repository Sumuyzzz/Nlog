写代码的时候看到`vue.$route`和`vue.$router`不清楚他们的区别，查了下资料整理一下，避免遗忘

## route

一个路由对象，显示当前激活路由的状态信息，路由对象是不可变的，每次成功的导航后都会产生一个新的对象。每个对象都是局部的，可以获取当前路由的 path, name, params, query 等属性。





## router

全局的router实例，通过vue根实例注入router实例，然后在注入到每个子组件。拥有许多属性和对象，任何页面也都可以调用其 push(), replace(), go() 等方法。







参考：[路由对象](https://router.vuejs.org/zh/api/#%E8%B7%AF%E7%94%B1%E5%AF%B9%E8%B1%A1)，[实例属性](https://router.vuejs.org/zh/api/#router-%E5%AE%9E%E4%BE%8B%E5%B1%9E%E6%80%A7),[实例方法](https://router.vuejs.org/zh/api/#router-%E5%AE%9E%E4%BE%8B%E6%96%B9%E6%B3%95)

