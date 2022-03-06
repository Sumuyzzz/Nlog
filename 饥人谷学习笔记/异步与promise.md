# 同步与异步

### 如果能拿到结果就是同步

比如你去医院挂号,你拿到好才会离开窗口

总之不拿到号码就不离开

### 反之就是异步

比如你在餐厅等位,那号码就可以逛街

如果每隔一段时间询问就是(轮询)

还有扫码微信等通知就是(回调)





### 以AJAX为例子

request.send()结束之后,并不能直接得到response

用console.log(requset.response)试验

必须要等到readyState变为4以后,浏览器才回头调用request.onreadystatechang函数







