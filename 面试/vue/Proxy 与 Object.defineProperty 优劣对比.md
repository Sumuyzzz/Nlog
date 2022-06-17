Proxy:
* 直接监听对象非属性
* 可直接监听数组变化
* 13中拦截方法，这些都是Object.defineProperty 不具备的
*  Proxy 返回的是一个新对象,我们可以只操作新的对象达到目的,而 Object.defineProperty 只能遍历对象属性直接修改
* 

Object.defineProperty：
* 兼容性好，支持IE9.



总结：


