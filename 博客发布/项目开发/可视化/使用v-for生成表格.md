背景



模拟数据如下

```js
const thead = ["单位名", "网关数", "设备数", "数据点", "报警", "操作"]

const items = [
  {
    name: "宝钢",

    value: 200,

    device: 400,

    stronghold: 5000,

    alarm: "无",
  },
  {
    name: "造纸厂",

    value: 3000,

    device: 2000,

    stronghold: 1000,

    alarm: "温度上限报警>120",
  },
  {
    name: "宝钢",

    value: 200,

    device: 400,

    stronghold: 5000,

    alarm: "无",
  },
]

const buttons = ["报警记录", "历史数据", "组态应用"]


```
实现思路
1. 通过v-for 来生成tr
2. 在里面使用v-for来生成td


最后奇怪的是button数据自动填补了




后续代码如下

```html

;<table>
  <thead>
    <tr>
      <th colspan="6">
        <Icon icon="fad:logo-reason" />
        监控列表
      </th>
    </tr>
  </thead>
  <tbody class="body">
    <tr class="first">
      <td v-for="th in thead">{{ th }}</td>
    </tr>

    <tr v-for="item in items">
      <td v-for="i in item">{{ i }}</td>

      <td>
        <button v-for="button in buttons">{{ button }}</button>
      </td>
    </tr>
  </tbody>
</table>

```


效果如下

![[Pasted image 20220612222433.png]]


接着实现无限滚动

需求：
1. 只有三行数据
2. 无缝，无限，自动滚动





思路一：
使用transfrom来移动自身数据

1. 绑定class
```html
;<tr v-for="item in items" class="scroll">
  <td v-for="i in item">{{ i }}</td>

  <td>
    <button v-for="button in buttons">{{ button }}</button>
  </td>
</tr>

```

```css
  

.scroll{

 transform: translate(0,50%);

}

```


效果：
![[Pasted image 20220612235422.png]]


表格边框无法跟随数据移动


……


世上无难事，只要换种方式

思路二：使用插件实现

```sh
npm install vue3-seamless-scroll
```




效果如下：

![[auto-scrool.gif]]

代码如下：

```vue

<template>

 <table>

 <thead>

 <tr>

 <th colspan="6">

 <Icon icon="fad:logo-reason" />

 监控列表

 </th>

 </tr>

 </thead>

 <tbody class="body">

 <tr class="first">

 <td v-for="th in thead">

 {{ th }}

 </td>

 </tr>

  

 <vue3-seamless-scroll :list="items" class="scroll">

 <tr v-for="item in items" class="item">

 <td v-for="i in item">

 {{ i }}

 </td>

 <td>

 <button v-for="button in buttons">

 {{ button }}

 </button>

 </td>

 </tr>

 </vue3-seamless-scroll>

  
  

 </tbody>

 </table>

</template>
```

为什么会独占一格呢


原因是有一层不明div包裹住了tr导致无法生成正确的tr


处理1：
使用ul模拟tr,li模拟td

结果失败
原因：
1. 无法自适应表格，表格数据一旦发生改变，就得重新布局



处理2：
使用absolute固定位置

![[Pasted image 20220613105410.png]]




失败

原因：
1. 当元素脱离文档流后，结构发生改变，无法自适应表格
2. 父元素需要padding来腾出位置，使得无法做到无缝滚动数据


处理3：






