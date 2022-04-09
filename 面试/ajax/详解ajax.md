## 简述
即异步的`JavaScript` 和`XML`(JSON)，是一种创建交互式网页应用的网页开发技术，可以在不重新加载整个网页的情况下，与服务器交换数据，并且更新部分网页


### 实现
1. 创建XMLHttpRequest对象
2. 设置响应 HTTP 请求状态变化的函数
3. 创建请求，指定方法和路径并发送请求
4. 根据响应 HTTP 请求状态变化的函数，获取数据
5. 最后实现局部刷新

```js
const request = new XMLHttpRequest()
request.onreadystatechange = function(e){
    if(request.readyState === 4){ 
        if(request.status >= 200 && request.status <= 300){
            console.log(request.responseText) // 
        }else if(request.status >=400){
            console.log("错误信息：" + request.status)
        }
    }
}
request.open('POST','http://xxxx')
request.send()
```


#### readyState

-   0: 请求未初始化
-   1: 服务器连接已建立
-   2: 请求已接收
-   3: 请求处理中
-   4: 请求已完成，且响应已就绪

#### open
简述：使用指定参数，初始化一个XMLHttpRequest实例对象

常见参数：
* method:需要使用的请求方法
* url:和页面同源的路径


#### send
简述：用于发送htpp请求,参数可选，默认只有url


参考
[# XMLHttpRequest 对象](https://wangdoc.com/javascript/bom/xmlhttprequest.html)
[# XMLHttpRequest](https://developer.mozilla.org/zh-CN/docs/Web/API/XMLHttpRequest)
