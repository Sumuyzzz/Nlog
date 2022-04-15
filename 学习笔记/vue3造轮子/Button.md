# 创建Button

## 设计Button

```vue
<Button
        @click=?
        @focus=?
        @mouseover=?
        theme="button or link or text"
        level="main or normal or minor"
        size="big normal small"
        disabled
        loading
        >
</Button>
```

## 代码实现

ButtonDemo.vue组件

```vue
<template>
	<div>Button实例</div>
	<h1>实例1</h1>
	<div>
		<Button @click="onClick">你好</Button>//这里传入了一个onclick事件
	</div>
</template>

<script lang="ts">
	import Button from "../lib/Button.vue";

	export default {
		components: { Button },
		setup() {
			const onClick = () => {
				console.log("hi");
			};
			return { onClick };
		},
	};
</script>

<style>
</style>
```

Button.vue组件

```vue
<template>
	<div>//默认组件的最外层接收这个事件
		<button><slot></slot></button>
	</div>
</template>

<script lang="ts">
	export default {
	inheritAttrs:false//在这里把属性继承关掉
	};
</script>

<style lang="scss" scoped>
	div {
		border: 1px solid red;
	}
</style>
```

![image-20210504144139369](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210504144139369.png)

所以点击组件的最外层会触发点击事件,怎么解决这个问题呢

1. 先用`inheritAttrs:false`把属性继承关掉,然后在向Button按钮添加一个` v-bind="$attrs`属性继承

