## 什么是Virtual DOM

Virtual DOM是对DOM的抽象，本质上是JavaScript对象，这个对象就是更加轻量级的对DOM的描述，提高重绘性能。
Virtual DOM 就是用一个原生的 JS 对象去描述一个 DOM 节点

## 关于dom和虚拟dom的区别

代码演示:

```html
<ul id='list'>  <li class='item'>itemA</li>  <li class='item'>itemB</li> </ul>
```

dom操作:

```js
let ulDom = document.getElementById('list');
console.log(ulDom);
```

虚拟dom操作:

```js
{  
    tag:'ul',  // 元素的标签类型
    attrs:{  //  表示指定元素身上的属性
        id:'list'
    },
    children:[  // ul元素的子节点
        {
            tag: 'li',
            attrs:{
                className:'item'
            },
            children:['itemA']
        },
        {   tag: 'li',
            attrs:{
                className:'item'
            },
            children:['itemB']
        }
    ]
}
```



### 虚拟dom的缺点

- 首次渲染大量 DOM 时，由于多了一层虚拟 DOM 的计算，会比 innerHTML 插入慢。虚拟 DOM 需要在内存中的维护一份 DOM 的副本。
- 如果你的场景是虚拟 DOM 大量更改，这是合适的。但是单一的，频繁的更新的话，虚拟 DOM 将会花费更多的时间处理计算的工作。比如，你有一个 DOM 节点相对较少页面，用虚拟 DOM，它实际上有可能会更慢。但对于大多数单页面应用，这应该都会更快。这也是为啥react和vue中的更新用了异步的方法，频繁更新时，只更新最后一次的。

### 总结：

- 虚拟dom是一个js对象
- DOM操作是”昂贵“的，js运行效率高
- 尽量减少DOM操作，而不是”推到重来“
- 项目越复杂，影响越严重
- 更好的跨平台

## 什么是diff算法

> 是用来对比差异的算法，有 linux命令 `diff`（我们dos命令中执行diff 两个文件可以比较出两个文件的不同）、git命令`git diff`、可视化diff(github、gitlab...)等各种实现。





**特点:**

- 只会做同级比较，不做跨级比较
- 比较后几种情况
  - `if (oldVnode === vnode)`，他们的引用一致，可以认为没有变化。
  - `if(oldVnode.text !== null && vnode.text !== null && oldVnode.text !== vnode.text)`，文本节点的比较，需要修改，则会调用`Node.textContent = vnode.text`。
  - `if( oldCh && ch && oldCh !== ch )`, 两个节点都有子节点，而且它们不一样，这样我们会调用`updateChildren`函数比较子节点，这是diff的核心
  - `else if (ch)`，只有新的节点有子节点，调用`createEle(vnode)`，`vnode.el`已经引用了老的dom节点，`createEle`函数会在老dom节点上添加子节点。
  - `else if (oldCh)`，新节点没有子节点，老节点有子节点，直接删除老节点。

##### key的作用

设置key和不设置key的区别：
 不设key，newCh和oldCh只会进行头尾两端的相互比较，设key后，除了头尾两端的比较外，还会从用key生成的对象`oldKeyToIdx`中查找匹配的节点，所以为节点设置key可以更高效的利用dom

如我们希望可以在B和C之间加一个F，Diff算法默认执行起来是这样的：

![img](https://pic2.zhimg.com/80/v2-bf76311258f100b789226ccbb2600071_hd.png)

即把C更新成F，D更新成C，E更新成D，最后再插入E，是不是很没有效率？

所以我们需要使用key来给每个节点做一个唯一标识，Diff算法就可以正确的识别此节点，找到正确的位置区插入新的节点。

![img](https://pic1.zhimg.com/80/v2-bb1147af7c458f0b09d6a3c2f74b0100_hd.png) ![img](https://pic1.zhimg.com/80/v2-bb1147af7c458f0b09d6a3c2f74b0100_hd.png) 所以一句话，key的作用主要是为了高效的更新虚拟DOM。另外vue中在使用相同标签名元素的过渡切换时，也会使用到key属性，其目的也是为了让vue可以区分它们，否则vue只会替换其内部属性而不会触发过渡效果

#### 总结

- 尽量不要跨层级的修改dom
- 在开发组件时，保持稳定的 DOM 结构会有助于性能的提升
- 设置key可以让diff更高效