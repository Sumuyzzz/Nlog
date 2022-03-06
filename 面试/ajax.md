

## 什么是Ajax

AJAX即“Asynchronous Javascript And XML”，是指一种创建交互式网页应用的网页开发技术。**指的是通过 JavaScript 的异步通信，从服务器获取 XML 文档从中提取数据，再更新当前网页的对应部分，而不用刷新整个网页。**

指的是通过 JavaScript 的异步通信，从服务器获取 XML 文档从中提取数据，再更新当前网页的对应部分，而不用刷新整个网页。



AJAX 包括以下几个步骤。

1. 创建XMLHttpRequest实例
2. 发出HTTP请求
3. 接收服务器传回的数据
4. 更新网页数据



## 什么是XML

XML即“E**x**tensible **M**arkup **L**anguage",是一种标记语言，**用于传送和携带数据信息**，区别于HTML用于展示数据，没有预定义标签,可自定义标签,像vue就是使用xml。

然而，**现在所说的xml指的就是json**.



## Ajax原理是什么

![img](https://p1-jj.byteimg.com/tos-cn-i-t2oaga2asx/gold-user-assets/2018/12/18/167bd019240a457b~tplv-t2oaga2asx-watermark.awebp)

![img](https://p1-jj.byteimg.com/tos-cn-i-t2oaga2asx/gold-user-assets/2018/12/18/167bd023855c0bf7~tplv-t2oaga2asx-watermark.awebp)



## AJAX的特点

### 优点

1. 无需刷新页面与服务器进行通信
2. 可以根据用户需求，更新一小部分

### 缺点

1. 没有浏览历史，不可回退（也就说浏览器左上角点不了）
2. 存在跨域问题
3. SEO不友好



## 什么是HTTP

HTTP（hypertext transprot protocol）超文本传输协议，协议规定了浏览器和万维网服务器之间相互通信的规则



### 请求报文

重点是格式与参数

主要分为： 

* 行 ：有POST和GET
* 头 ：
* 空行 
* 体（当请求行为GET时，为空）

```http
POST /s?ie=utf-8 HTTP/1.1 //行
Host:atguigu.com //头
Cookie:name=guigu //头
Content-Type:application/x-www-form-urlencoded
User-Agent:chrome 83
空行
username=admin&password=admin
```





### 响应报文

主要有：

* 行
* 头
* 空行
* 体



```http
HTTP/1.1 200 OK //行
Content-Type:text/html;charset=utf-8 //头
Content-length:2048 //头
Content-encoding:gzip //头
空行
```

下面是响应体，其实是html页面内容

```html
<html>
    <head>
        <body>
            <h1>hi</h1>
        </body>
    </head>
</html>
```

一般ajax向服务端发送请求得到的内容，就呈现在响应体里









## get和post的区别

- GET 用于获取信息，是无副作用的，是幂等的，且可缓存
- POST 用于修改服务器上的数据，有副作用，非幂等，不可缓存







[ajax进化史](https://mieruko0713.github.io/2018/01/02/network/)





## 什么是fetch





