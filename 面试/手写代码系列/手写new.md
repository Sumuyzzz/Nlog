### new的实质



```js
function _new(Constructor,...arg) {
    
    let instance = Object.create(Constructor.prototype)

    let result = Constructor.apply(instance,arg)

    return typeof result==='object'?result:instance
    
}
```

