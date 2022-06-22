## 介绍
promise是异步编程的一种解决方案，比起传统回调，更简洁，更合理。


Promise其实是一个容器，装载着异步事件。根据规则来执行相应的事件。


特点：

* 拥有三种状态，分别是：`pending`(等待执行中)，`fulfilled`（已成功），`rejucted`(已失败)。
* 不受外界影响，一旦进入某个状态，任何操作都无法改变这个状态。



### then
接收两个回调参数，

语法如下

```js
promise.then(
	(result)=>{},
	(error)=>{}
)
```


如果只接受结果

```js
promise.then(result)

```


### catch





### finaly


```js
new Promise((resolve, reject) => { 
}) ;
.finally(() => stop loading indicator) 
.then(result => show result, err => show error)


```



