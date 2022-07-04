### 一、GET
用于向服务器查询信息，将参数放入URL末尾，发送给服务器
```js
fetch('https://jsonplaceholder.typicode.com/todos/')
.then(response=>response.json())
.then(data=>console.log(data))
```
![](https://s2.loli.net/2022/06/29/wVhl7xf8COSaJuZ.png)


### 二、POST
Post 用于将数据发送到服务器，将数据包含在请求体中，例如表单提交或者上传文件。
```js
fetch('https://jsonplaceholder.typicode.com/todos',{
    method:'POST',
    headers:{'content-types':'application/json'},
    body:JSON.stringify({
        userId:6,
        id:300,
        title:'Learn fetch application',
        completed:false
    })
})
.then(response=>response.json())
.then(data=>console.log(data))
```

![](https://cdn.jsdelivr.net/gh/Sumuyzzz/pictures/img/202207022345645.png)

### 三、PUT
```js
fetch('https://jsonplaceholder.typicode.com/todos/5',{
    method:'PUT',
    headers:{'content-type':'application/json'},
    body:JSON.stringify({
        userId:1,
        id:15,
        title:'hello fetch api',
        completed:false
    })
})
.then(response=>response.json())
.then(data=>console.log(data))
```

![](https://s2.loli.net/2022/06/29/Qk3vLYiFOPUmnxz.png)


### 四、PATCH
PATCH 方法用于更新资源属性的值。
```js
fetch('https://jsonplaceholder.typicode.com/todos/1',{
      method:'PATCH',
      headers:{'Content-type':'application/json'},
      body:JSON.stringify({
          completed:true,
          title:'we are going to learn PATCH method'
      })
})
.then(response=>response.json())
.then(data=>console.log(data))


```

![[Pasted image 20220629193001.png]]


### 五、DELETE
DELETE 方法用于删除由其 URI 指定的资源。


```js
fetch('https://jsonplaceholder.typicode.com/todos/1',{
    method:'DELETE'
})
.then(response=>response.json())
.then(data=>console.log(data))

```
![](https://cdn.jsdelivr.net/gh/Sumuyzzz/pictures/img/202207011846004.png)




### POST,PUT和PATCH的区别

`HTTP`请求方法 `POST` 通常用于**资源创建**，而 `PUT` 用于**资源更新**。
虽然这在大多数情况下都很好，但使用 `PUT` 来创建资源也是可行的。
`PATCH` 是资源更新的替代方案，因为它允许**部分更新**。

#### 幂等性
一个 HTTP 方法是**幂等**的，指的是同样的请求被执行一次与连续执行多次的效果是一样的，服务器的状态也是一样的。


在正确实现的条件下， [`GET`](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Methods/GET) ， [`HEAD`](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Methods/HEAD) ， [`PUT`](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Methods/PUT) 和 [`DELETE`](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Methods/DELETE) 等方法都是**幂等**的，而 [`POST`](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Methods/POST) 方法不是。所以多次发送相同的 POST 请求会导致创建多个资源。

#### POST和PUT

由于`POST`不是**幂等**的，提交多次会创建多个资源，并不会在现有基础上更新，但`PUT`可以用于创建和更新资源。

`PUT`在请求数据时，会根据`标识符`判断是否存在该信息，如果存在则创建或者替换。

`POST`在请求数据时，如果没有`标识符`，会创建新的标识符，如果再次请求**相同数据**没有`标识符`，会再次创建新的标识符。


#### PUT VS PATCH
`PATCH`和`POST`一样不是`幂等`的，但可以根据传递参数修改部分信息。

`PATCH`在请求数据时，会根据`标识符`判断是否存在该数据，然后修改部分信息，否则**抛出异常**






![](https://cdn.jsdelivr.net/gh/Sumuyzzz/pictures/img/202207030212297.png)



### 总结
1.  用于**创建新数据发送服务器** =>POST
2.  用于**读取数据**=>GET
3.  如果数据存在则更新，否则创建数据=>PUT
4.  和PUT类似，不同之处在于**PUT用于更新完整信息**，PATCH只需要**修改部分数据**=>PATCH
5.  **删除某个数据**=>DELETE



### 参考
[# REST / HTTP methods: POST vs. PUT vs. PATCH](https://www.mscharhag.com/api-design/http-post-put-patch)
[[post和get]]
[{JSON} Placeholder](https://jsonplaceholder.typicode.com/)
[# [What is the difference between PUT, POST and PATCH?](https://stackoverflow.com/questions/31089221/what-is-the-difference-between-put-post-and-patch)](https://stackoverflow.com/questions/31089221/what-is-the-difference-between-put-post-and-patch)
[# REST – PUT vs POST](https://restfulapi.net/rest-put-vs-post/)
[](https://developer.mozilla.org/zh-CN/docs/Glossary/Idempotent)
