问题：使用scrollToElement时，没有跳转至相应的节点

![](https://cdn.jsdelivr.net/gh/Sumuyzzz/pictures/img/202207180318409.gif)



猜想：
不用想了，找到答案了。
原因是传递的dom有问题。

子组件定义
```vue
<template>

 <div class="list" @click="handleClick">

 <div class="item" v-for="(item, key) in props.cities" :key="key">{{ key }}</div>

 </div>

</template>

  

<script setup>

  
  
const props = defineProps({

 cities: {

 type: Object,

 default: ''

 },

})

  
  

const emit = defineEmits(['itemKey'])

  
  

const handleClick = (e) => {

 emit('itemKey', e.target) //原因是e.target并不是父组件所滚动的标题元素，而是点击的dom元素

}


```
