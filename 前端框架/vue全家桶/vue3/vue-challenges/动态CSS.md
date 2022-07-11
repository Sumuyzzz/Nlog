## [CSS 中的 `v-bind()`](https://staging-cn.vuejs.org/api/sfc-css-features.html#v-bind-in-css)
单文件组件的 `<style>` 标签支持使用 `v-bind` CSS 函数将 CSS 的值链接到动态的组件状态



```vue
<script setup>
import { ref } from "vue"
const theme = ref("red")
const colors = ["blue", "yellow", "red", "green"]
setInterval(() => {
  theme.value = colors[Math.floor(Math.random() * 4)]
}, 1000)
</script>
<template>
  <p>hello</p>
</template>
<style scoped>
/* Modify the code to bind the dynamic color */
p {
  color: v-bind(theme);
}
</style>

```

![](https://cdn.jsdelivr.net/gh/Sumuyzzz/pictures/img/202207061243106.gif)