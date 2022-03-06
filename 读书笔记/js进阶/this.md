this注意区分的场景

1. ```js
   function Foo(){
       this.user='foo'
       const o = {}
       return o
   }
   const instance = new Foo()
   console.log(instance.user) //undefined
   console.log(instance) //{}
   ```

2. ```js
   function Foo(){
       this.user='foo'
       return 1
   }
   const instance = new Foo()
   console.log(instance.user) //'foo'
   ```

   结论：构造函数返回值如果是对象，this就会指向这个返回值，否则指向实例。

   





我们常常把call、apply、bind、new对this的绑定称为显式绑定，根据调用关系确定称为隐式绑定

这两个谁优先级更高呢

```js
functon foo(a){
    console.log(this.a)
}

const obj1 = {
    a:1,
    foo:foo
}

const obj2 ={
    a:2,
    foo:foo
}
obj1.foo.call(obj2) //2
obj2.foo.call(obj1) //1

```

答案是显式绑定优先级高

