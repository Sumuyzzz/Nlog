定义：翻译为代理，就是对对象实行一个代理监听的作用

使用：接受两个参数，

* `target`:目标代理对象

* `handler`:处理函数

```js
var proxy = new Proxy(target, handler);
```

```js
let target = {
    name: 'Tom',
    age: 24
}
let handler = {
    get: function(target, key) {
        console.log('getting '+key);
        return target[key]; // 不是target.key
    },
    set: function(target, key, value) {
        console.log('setting '+key);
        target[key] = value;
    }
}

let proxy = new Proxy(target, handler)
proxy.name     // 实际执行 handler.get
proxy.age = 25 // 实际执行 handler.set
```





实例方法：

* get：