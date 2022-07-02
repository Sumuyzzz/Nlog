### 一、GET
用于读取接口信息
```js
fetch('https://jsonplaceholder.typicode.com/todos/')
.then(response=>response.json())
.then(data=>console.log(data))
```
![](https://s2.loli.net/2022/06/29/wVhl7xf8COSaJuZ.png)


### 二、PST
Post 用于将数据发送到服务器，例如上传文件或传输一些数据或将新行添加到后端表到任何类型的 Web 表单。
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




[

### POST,PUT和PATCH的区别

`HTTP`请求方法 `POST` 通常用于**资源创建**，而 `PUT` 用于**资源更新**。
虽然这在大多数情况下都很好，但使用 `PUT` 来创建资源也是可行的。
`PATCH` 是资源更新的替代方案，因为它允许**部分更新**。









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