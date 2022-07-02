`Vue`数据双向绑定原理是通过 **数据劫持结合发布者-订阅者模式** 的方式来实现的，首先是通过 `ES5` 提供的 `Object.defineProperty()` 方法来劫持（监听）各属性的 **getter、setter**，并在当监听的属性发生变动时通知订阅者，是否需要更新，若更新就会执行对应的更新函数。


#### 发布者订阅者模式
##### 实现一个 Observer

```js

class Observer {
	consturct(data){
	this.data = data
	this.walk(data)
	}
	walk(data){
		Object.keys(data).forEach(()=>{
			this.defineReactive(data,key,data[key])
		})
	}
	defineReative(data,key,val){
	const  dep = new Dep()
	const  childObj = observe(val){
		this.defineProperty(data, key, {
            enumerable: true,
            configurable: true,
            get: function getter () {
                if (Dep.target) {
                    // 在这里添加一个订阅者
                    console.log(Dep.target)
                    dep.addSub(Dep.target);
                }
                return val;
            },
            set: function setter (newVal) {
                if (newVal === val) {
                    return;
                }
                val = newVal;
                // 新的值是object的话，进行监听
                childObj = observe(newVal);
                dep.notify();
            }
	}
	}
}



```

**Vue响应式原理总结**

-   Object.defineProperty - get ，用于 依赖收集
    
-   Object.defineProperty - set，用于 依赖更新
    
-   每个 data 声明的属性，都拥有一个的专属依赖收集器 Dep.subs
    
-   依赖收集器 subs 保存的依赖是 watcher
    
-   watcher可用于 进行视图更新