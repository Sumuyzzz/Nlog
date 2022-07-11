## isRef()

检查某个值是否为 ref。



## unref()

如果参数是 ref，则返回内部值，否则返回参数本身。这是 `val = isRef(val) ? val.value : val` 计算的一个语法糖。


## toRef()
可用于为响应式对象上的 property 创建 ref。



```vue
<script setup lang="ts">
import { ref, Ref, reactive,isRef, unref,toRef } from "vue"

const initial = ref(10)
const count = ref(0)

// Challenge 1: Update ref
function update(value) {
  // impl...
  count.value = value
}

/**
 * Challenge 2: Checks if `count` is a ref object.
 * Make the output to be 1
*/
console.log(
  // impl ? 1 : 0
  isRef(count)?1:0
)

/**
 * Challenge 3: Unwrap ref
 * Make the output to be true
*/
function initialCount(value: number | Ref<number>) {
  // Make the output to be true
  console.log(value === 10)
}

initialCount(unref(initial))

/**
 * Challenge 4:
 * create a ref for a property on a source reactive object.
 * The created ref is synced with its source property:
 * mutating the source property will update the ref, and vice-versa.
 * Make the output to be true
*/
const state = reactive({
  foo: 1,
  bar: 2,
})
const fooRef = toRef(state,'foo') // change the impl...

// mutating the ref updates the original
fooRef.value++
console.log(state.foo === 2)

// mutating the original also updates the ref
state.foo++
console.log(fooRef.value === 3)

</script>

<template>
  <div>
    <p>
      <span @click="update(count-1)">-</span>
      {{ count }}
      <span @click="update(count+1)">+</span>
    </p>
  </div>
</template>


```