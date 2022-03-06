```html
<body>
    <div id='app'>
        {{a}}//输出100
    </div>
    <div id='aqq'>
        {{a}}//输出{{a}}
    </div>
</body>
<script src="vue.js">
let vue=new Vue({
    //挂载点,所有vue方法和属性都必须在内部使用
    el:'#app',
    //数据管理仓库,所有vue数据都在data里面
    data:{
        a:100
    }
})
</script>
```



	table



Prop 是你可以在组件上注册的一些自定义 attribute。
