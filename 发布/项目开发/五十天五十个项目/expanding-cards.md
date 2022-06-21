`
效果图


![[Expanding Cards.gif]]


准备`html`模板如下

使用`li`列表来嵌入图片
```html
<!DOCTYPE html>

<html lang="en">

<head>

<meta charset="UTF-8" />

<meta name="viewport" content="width=device-width, initial-scale=1.0" />

<link rel="stylesheet" href="style.css" />

<title>Expanding Cards</title>

</head>

<body>

<div class="container">

<div class="panel active" style="background-image: url('https://images.unsplash.com/photo-1558979158-65a1eaa08691?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1350&q=80')">

<h3>Explore The World</h3>

</div>

<div class="panel" style="background-image: url('https://images.unsplash.com/photo-1572276596237-5db2c3e16c5d?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1350&q=80')">

<h3>Wild Forest</h3>

</div>

<div class="panel" style="background-image: url('https://images.unsplash.com/photo-1507525428034-b723cf961d3e?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1353&q=80')">

<h3>Sunny Beach</h3>

</div>

<div class="panel" style="background-image: url('https://images.unsplash.com/photo-1551009175-8a68da93d5f9?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1351&q=80')">

<h3>City on Winter</h3>

</div>

<div class="panel" style="background-image: url('https://images.unsplash.com/photo-1549880338-65ddcdfd017b?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1350&q=80')">

<h3>Mountains - Clouds</h3>

</div>

</div>

<script src="script.js"></script>

</body>

</html>
```


css实现思路如下

```scss



```

js实现思路如下：
遍历所有的li，每个li绑定一个事件，点击响应的li,添加样式，并解绑

```js





```