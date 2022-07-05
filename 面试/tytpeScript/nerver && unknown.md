



## nerver
介绍：一个**永远不会存在值**的类型，类似undefined，属于不存在的属性。

例子：
当变量作为void类型时，可以赋值为null，但是nerver就不行。

```ts

let something: void = null;
let nothing: never = null; 
// Error: Type 'null' is not assignable to type 'never'
  
```

当某个事件确定不会发生时，可以使用nerver类型。
```ts
function throwError(errorMsg: string): never { 
            throw new Error(errorMsg); 
} 

function keepProcessing(): never { 
            while (true) { 
         console.log('I always does something and never ends.')
     }
} 
```

## any

介绍：表示**任意类型**，不声明类型时的任意类型，不受任何约束，编译时会跳过类型检查。

例子：

```ts
let value:any  
value = 'foo' 
value = 1

value.toString() //'1'

value = false

let value2:any = value


const array:any[]=['foo',1,false]

```


## unknown

介绍：表示**未知的类型**，类似`any`类型的收窄，因为官网不提倡使用`any`，你可以理解为`any`的安全版

例子：

```ts
let value: unknown;

value = 'foo' 
value = 1


value.toString() //error

value = false

let value2:unknown = value //eroor




const array:any[]=['foo',1,false]

```



## void
介绍：表示无**任何类型**，类似无返回值的函数
例子：

```ts

type VoidFn = ()=>void

const voidFn:VoidFn()=>{}

//或者

const voidFn:VoidFn()=>{
	return 
}
//或者

const voidFn:VoidFn()=>{
	return undefined
}


```





[# TypeScript 中类型 any，void，unknown，never之间的区别](https://blog.csdn.net/KNIGH_YUN/article/details/115412962)

[# When to use `never` and `unknown` in TypeScript](https://blog.logrocket.com/when-to-use-never-and-unknown-in-typescript-5e4d6c5799ad/)