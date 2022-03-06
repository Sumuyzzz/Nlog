## iterator(可迭代对象)

特点：

* 对象的值可迭代

例如：数组，字符串，Set,Map





## 创建可迭代对象

当你定义的对象不是可迭代对象时，可以使用Symbol.iterator 属性，让它变成可迭代对象

```js
let collection = {
    item: [],
    *[Symbol.iterator](){
        for(let item of this.items){
            yield item;
        }
    }
}

collection.items.push(1);
collection.items.push(2);
collection.items.push(3);

for (let x of collection) {
	console.log(x);
}

```



