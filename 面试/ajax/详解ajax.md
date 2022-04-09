即异步的`JavaScript` 和`XML`(JSON)，是一种创建交互式网页应用的网页开发技术，可以在不重新加载整个网页的情况下，与服务器交换数据，并且更新部分网页


### 实现
1. 创建XMLHttpRequest对象
2. 设置onreadystatechange 事件,当readuStat



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