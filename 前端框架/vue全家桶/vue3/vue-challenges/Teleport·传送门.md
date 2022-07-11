`<Teleport>` 是一个内置组件，使我们可以将一个组件的一部分模板“传送”到该组件的 DOM 层次结构之外的 DOM 节点中。


为 `<Teleport>` 指定的目标 `to` 期望接收一个 CSS 选择器字符串或者一个真实的 DOM 节点。



![](https://cdn.jsdelivr.net/gh/Sumuyzzz/pictures/img/202207060636284.png)
```vue

<script setup>
import { ref } from 'vue'

const open = ref(false)
</script>

<template>
<button @click="open = true">Open Modal</button>

<div id="demo">
  <div>
    {{open}}	
  </div>
  </div>
  
<Teleport to="#demo">
  <div v-if="open" class="modal">
    <p>Hello from the modal!</p>
    <button @click="open = false">Close</button>
  </div>
</Teleport>
</template>

<style scoped>
.modal {
  position: fixed;
  z-index: 999;
  top: 20%;
  left: 50%;
  width: 300px;
  margin-left: -150px;
}
  #demo{
    border:1px solid red;
    overflow:auto;
  }

</style>


```



效果图：


![](https://cdn.jsdelivr.net/gh/Sumuyzzz/pictures/img/202207060637487.gif)