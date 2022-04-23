发布订阅也叫观察者

一般B站用户关注了up，当它发布的视频之后，用户就可以在动态查看视频推送，避免了经常访问关注的up的主页列表去获取视频。

优点：
* 广泛应用与异步编程
* 不需要关注内部状态，只关心时间点


on:订阅，绑定一次，每次发布都有效
emit:发布
once:单次订阅,绑定几次输出几次
off:取消订阅


```js

class EventEmitter {

 constructor() {

 this.events = Object.create(null)

 }

 on(target, handle) {

 this.events[target] = this.events[target] || []

 this.events[target].push(handle)

 return this

 }

  

 off(target, handle) {

 this.events[target] = this.events[target].filter(func => func !== handle)

 return this

 }

  

 emit(target, ...args) {

 this.events[target].map(fnc => {

 fnc.apply(null, args)

 })

 return this

 }

 once(target, handle) {

 const wrapper = (...args) => {

 this.off(target, w)

 handle.apply(this, args)

 }

 this.on(target, wrapper)

 return this

 }

}

  
  
  
  

let eventEmitter = new EventEmitter();

  
  

eventEmitter.once('onemore', function () {

 console.log(111);

});

eventEmitter.once('onemore', function () {

 console.log(111);

});

eventEmitter.on('onemore', function () {

 console.log('看这个');

});


eventEmitter.emit('onemore');

eventEmitter.emit('onemore');

eventEmitter.emit('onemore');

eventEmitter.emit('onemore');

eventEmitter.emit('onemore');

eventEmitter.emit('onemore');


```





结果

```js

111
111
看这个
看这个
看这个
看这个
看这个
看这个

```



参考
[# 手写EventEmitter事件巴士](https://www.favori.cn/nodejs-event-emitter)

[## 手动实现EventEmitter](https://github.com/ConardLi/awesome-coding-js/blob/master/JavaScript/EventEmitter.md)