## 起因

今天使用post方法出现了这个问题

<img src="C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220304150319280.png" alt="image-20220304150319280" style="zoom: 200%;" />



接着根据它提供的error定位到![image-20220304150444045](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220304150444045.png)



## 开始解决

起初以为内容格式不对，把里面的内容删掉，但问题还是没有解决

![image-20220304150617717](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220304150617717.png)

![image-20220304150657245](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220304150657245.png)

正当我开始迷茫的时候，翻到了阮一峰老师写的一篇跨域博客，里面讲了两种请求，其中一种简单请求，规定HTTP的头信息不超出以下几种字段：

- Accept
- Accept-Language
- Content-Language
- Last-Event-ID
- Content-Type：只限于三个值`application/x-www-form-urlencoded`、`multipart/form-data`、`text/plain`





## 结果

然后我对比了一下代码，发现请求头信息错了，尝试修改，错误消除了，但是又试了其他两个值，中间的值不能用，后来查到，可以在服务端加上` *res*.setHeader('Access-Control-Allow-Headers', '*');`，实现任意请求头设置，但是有个预检，不给过，后来找到。all方法可以实现自定义请求头信息。

最后在这就停顿了。