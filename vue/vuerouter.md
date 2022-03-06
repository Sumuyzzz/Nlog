## Hash

特点:

* 丑
* 无法使用锚点定位



## History

* 需要后端配合,ie9不兼容(可强制使用刷新处理)

![image-20210618152754790](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210618152754790.png)



router-link,$router.push,...触发updateRoute改变响应式数据,路由通过Vue.util.defineReactive_route把route信息变成响应式的,router-view根据url匹配渲染的页面

