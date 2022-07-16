### Attribute Inheritance（属性继承）
当子组件只有一个根元素时，父组件传递的props属性会自动添加到根元素里。

子组件
```vue
<!-- template of <MyButton> -->
<button>click me</button>
```

父组件
```vue
<MyButton class="large" />
```

结果
```vue
<button class="large">click me</button>
```

### `class` and `style` Merging（类和样式合并）

如果子组件根元素存在属性，那么传递的class 或style将会添加到根元素里，那上个例子来改：

```vue
<!-- template of <MyButton> -->
<button class="btn">click me</button>
```
最后呢会变成这样子
```vue
<button class="btn large">click me</button>
```

### `v-on` Listener Inheritance（on监听器继承）
