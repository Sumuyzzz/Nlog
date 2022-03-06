## 是什么

对prop进行双向绑定，可实现子组件与父组件之间的数据同步

**父组件**

```vue
<Children :prop.sync='value'> </Children>

//相当于
<Children v-bind:porp='object.value' v-on:update:prop='object.value=$event'></Children>
```

**子组件**

```vue
<script>
export default {
  name: "Children",
  props: {
    prop: String,
  },
};
</script>
```



## 为什么

先说规则

* 父组件不能修改props的数据
* 只能通知子组件`emit`,触发`event`事件
* `event`可以获取`emit`传入的参数



然后就有这东西

```vue
<text-document
  v-bind:title="doc.title"
  v-on:update:title="doc.title = $event"
></text-document>
```

.sync就是这种模式的语法糖

```vue
<text-document v-bind:title.sync="doc.title"></text-document>
```



