如何解决登录信息更新的问题，使用eventbus

![](https://s2.loli.net/2022/06/28/4towMWvSszLJFa7.png)


由于写了个逻辑判断，只要登录过就不会更新用户名。

需要eventbus，订阅来绑定信息



```ts
export default class EventEmitter {
  static eventObject: any

  events: any

  constructor() {
    this.init()
  }

  init() {
    if (!EventEmitter.eventObject) {
      EventEmitter.eventObject = Object.create(null)

      this.events = EventEmitter.eventObject
    }
  }

  on(target: string, handle: (value: any) => void) {
    this.events[target] = this.events[target] || new Array()
    this.events[target].push(handle)

    return this
  }

  off(target: string, handle: (value: any) => void) {
    this.events[target] = this.events[target].filter(
      (func: () => void) => func !== handle
    )

    return this
  }

  emit(target: string, ...args: any) {
    this.events[target].map((handle: () => void) => {
      handle.apply(null, args)
    })

    return this
  }

  once(target: string, handle: (value: any) => void) {
    const wrapper = (...args: any) => {
      this.off(target, wrapper)

      handle.apply(this, args)
    }

    this.on(target, wrapper)

    return this
  }
}


```


