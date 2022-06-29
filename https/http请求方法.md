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



### 三、put
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


### 四、patch
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


### 五、delete
DELETE 方法用于删除由其 URI 指定的资源。


```js




```


### 总结


1.  Create NEW record =>POST
2.  read=>GET
3.  If the record exists then update else create a new record=>PUT
4.  update/modify=>PATCH
5.  delete=>DELETE




[{JSON} Placeholder](https://jsonplaceholder.typicode.com/)