### 单文件组件 `<script setup>`


`<script setup>`是在单文件中使用组合式API编译时的语法糖，相比普通`<script>`语法，它具有更多特性：

* 代码更简洁
* 能够使用纯Typescript 声明 props 和抛出事件
* 更好的 IDE 类型推断性能

#### 使用

将`setup`attribute添加到`<script>`上，

```vue
<script setup>
console.log('hello script setup')
</script>
```












### 参考

[# 单文件组件 `<script setup>`](https://staging-cn.vuejs.org/api/sfc-script-setup.html)