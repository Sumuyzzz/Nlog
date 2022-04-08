## 什么是express

`Express`框架是一款简洁而灵活的node.js web应用框架。

利用express框架可以减少我们的代码量


### 路由
路由是指URI的定义以及响应请求客户端的方式。

我们所使用的 app 与 HTTP 方法相对应的 Express 对象方法来定义路由，如 `app.get()` 用于处理 GET 请求，而 `app.post` 则用于处理 POST 请求。

示例

```javascript
var express = require('express');
var app = express();

// 当对主页发出 GET 请求时，响应“hello world”
app.get('/', function(req, res) {
  res.send('hello world');
});
```


有一种特殊路由方法：`app.all()`，它并非派生自 HTTP 方法。该方法用于在所有请求方法的路径中装入中间件函数。

```javascript
app.all('/secret', function (req, res, next) {
  console.log('Accessing the secret section ...');
  next(); // pass control to the next handler
});
```