
1. 使用ref绑定dom元素
2. 使用onMounted来获取



文档说明：
>注意，你只可以**在组件挂载后**才能访问 ref。

```vue
<script setup lang="ts">
import { ref, onMounted } from 'vue'

const el = ref<HTMLInputElement | null>(null)

onMounted(() => {
	console.log(el.value) //div element
})
console.log(el.value) //null

</script>

<template>
  <input ref="el" />
</template>
```