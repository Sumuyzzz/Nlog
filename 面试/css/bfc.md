## 全称:块级格式化上下文

先看两个概念：
* box:box是css布局的基本单位，一个页面由多个box组成，这个box就是我们所说的盒模型
* Block Formatting context ：块级格式化上下文，它是页面中的一块渲染区域，并且有一套渲染规则，它决定了其子元素该如何定位，以及其他元素的关系和相互作用。

通俗来讲：BFC是一个独立的布局环境，可以理解为一个容器，这个容器按照一定规则进行物品摆放，不会影响外部的其他环境。



规则如下：

1. 内部盒子会在垂直方向上一个接着一个的放置
2. **对同一BFC的两个相邻的盒子的margin会发生重叠**，与方向无关
3. BFC区域不会与float区域重叠
4. **每个元素的左外边距与包含块的左边界相接触（从左到右），即使浮动元素也是如此**
5. **计算BFC的高度时，浮动子元素也参与计算**
6. **BFC就是页面上的一个隔离独立容器**，容器里面子元素不会影响外面的元素，反之亦然



开启规则的方式：
* 浮动元素都可以开启，例如：`float`,`position:fixd`,`position:absolute/fixed`
* `display:flow-root`，这个类似根元素
* `overflow`
* `display:flex/grid`





## 应用场景：

1. [自适应两栏布局](https://codepen.io/sumuyzzz/pen/qBVyOjP)

规则：根据规则4，每个元素的margin box左边



处理：为了避免重叠，需要元素放在不同的bfc上，所以就可以把侧边栏固定宽度且左浮动，而对右侧内容触发 BFC，使得它的宽度自适应该行剩余宽度。

```html
<div class="contain">
  <div class="box1-contain">
      <div class="box1"></div>
  </div>
  <div class="box2-contain">
      <div class="box2"></div>
  </div>
</div>
```

```css
.contain{
  width:300px;
  border:1px solid red;
}

.box1{
  width:100px;
  height:100px;
  border:1px solid black;
  margin:10px;
  float:left;
}

.box2{
  width:100px;
  height:100px;
  margin:10px;
  border:1px solid black;
}

.box2-contain{
  overflow:hidden;
}
```

![image-20220303113501656](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220303113501656.png)





2. [防止`margin`合并](https://codepen.io/pen/)

应用原理：在同一BFC下垂直的margin会发生合并，需要两个元素处在不同的BFC下，可防止margin合并。

```html
<div class="layout">
    <div class="a">a</div>
    <div class="b">b</div>
</div>
```
```css
.a,
.b {
    width:100px;
    border: 1px solid #999;
    margin: 30px;
}

```
![image-20220303111816231](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220303111816231.png)

```html
<div class="contain-b">
    <div class="b">b</div>
</div>
```

```css
.contain-b {
    overflow: auto;
}
```

![image-20220303112528487](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220303112528487.png)

3. [清除浮动](https://codepen.io/sumuyzzz/pen/yLPGvVa)

规则：计算BFC高度时，浮动元素也会参与计算

原理：当父元素开启`overflow`时，子元素如果开启浮动，相应的父元素将其包裹住，**就会清除浮动**



```html
<div class="contain">
  <div class="box1 box"></div>
  <div class="box2 box"></div>
</div>
```

![image-20220303111354688](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220303111354688.png)



```css
.contain{
  width:300px;
  border:1px solid red;
/*   overflow:auto; */
}
.box{
  width:100px;
  height:100px;
  border:1px solid black;
  float:right;
}
```

![image-20220303111523479](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220303111523479.png)

4. 阻止元素被浮动元素覆盖

**规则：**

**原理：**

```html
<div class="contain">
  <div class="box1"></div>
  <div class="box2"></div>
</div>  
```

```css
.contain{
  width:400px;
  border:1px solid red;
}

.box1{
  width:100px;
  height:100px;

  background:#bfc;
  float:left;
}

.box2{
  width:300px;
  height:300px;

  background:#ffa;
/*   overflow:auto; */
}

```

![image-20220303120537898](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220303120537898.png)



**解决：**在兄弟元素加上`overflow`

![image-20220303120734265](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220303120734265.png)





## 参考链接

[根据规则解释BFC](https://juejin.cn/post/6844903476774830094)

[MDN](https://developer.mozilla.org/zh-CN/docs/Web/Guide/CSS/Block_formatting_context)

[十分钟理解BFC](https://zhuanlan.zhihu.com/p/25321647)

[深入理解BFC](https://juejin.cn/post/6844903693028966414)

[张鑫旭BFC](https://www.zhangxinxu.com/wordpress/2015/02/css-deep-understand-flow-bfc-column-two-auto-layout/)