# 什么是Promise

Promise是抽象异步处理对象以及对其进行各种操作的组件

```javascript
const p=new Promise((resolve,reject)=>{
    let a=1+1
    if(a==2){
        resolve('Success')
    }else{
        reject('Failed')
    }
})

p.then((message)=>{
    console.log('This is in the then '+message)
}).catch((message)=>{
    console.log('This is in the catch '+message)
})
```



```javascript
let recordOne=new Promise((resolve,reject)=>{
    resolve('1 Recorded')
})
let recordTwo=new Promise((resolve,reject)=>{
    resolve('2 Recorded')
})
let recordThree=new Promise((resolve,reject)=>{
    resolve('3 Recorded')
})

Promise.all([
    recordOne,
    recordTwo,
    recordThree
]).then((messages)=>{
    console.log(messages)
})// (3) ["1 Recorded", "2 Recorded", "3 Recorded"]

Promise.race([
    recordOne,
    recordTwo,
    recordThree
]).then((messages)=>{
    console.log(messages)
})//1 Recorded

```

