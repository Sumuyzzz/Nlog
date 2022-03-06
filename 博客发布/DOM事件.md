## DOM事件流

假如在一个button上注册一个click事件,又在其它父元素上div上注册了一个click时间,那么当我们点击button,先是触发**父元素上的事件**,还是**button上的事件**呢,这就需要一种约定去规范事件的执行顺序,就是事件执行的流程.

```jS
<div onclick="console.log('first div')">
  <div onclick="console.log('second div')">
    <button onclick="console.log('button')">
      Click!
    </button>
  </div>
</div>
```

当点击按钮时，event.target是什么？

导致事件的最深嵌套的元素是事件的 target。



### 事件触发三阶段

事件触发有三个阶段

- `window` 往事件触发处传播，遇到注册的捕获事件会触发
- 传播到事件触发处时触发注册的事件
- 从事件触发处往 `window` 传播，遇到注册的冒泡事件会触发



```js
<div onclick="console.log('div')">
  <p onclick="console.log('p')">
    Click here!
  </p>
</div>
```

现在输出的顺序是什么

在事件传播期间，有三个阶段：捕获、目标和冒泡。默认情况下，事件处理程序在冒泡阶段执行（除非将 `useCapture` 设置为 `true`）。它从嵌套最深的元素向外传播。
