# position

指定一个元素在文档中的位置，这是mdn的定义。

参数：

* **static**（默认）:**静态定位**，指定元素的正常显示
  * 参照物：无
* **relative**:**相对定位**，相对于之前位置的偏移量，相当于**灵魂出窍**，看见的只是元素的灵魂，肉身还占据文档的位置，也就是**元素不会脱离文档流**。
  * 参照物：自身
* **absolute**：**绝对定位**，指定元素在相对于最近的非static 定位祖先元素的偏移，也就是当本身元素设置`position：absolute`时，其父元素也开启除了**默认值**以外的定位。开启绝对定位的元素会脱离文档流，下面的元素会占据它的位置。
  * 参照物：开启定位的父元素
* **fixed**:**固定定位，**指定元素在窗口的位置，无论窗口如何滚动，**元素都会处于窗口的指定位置**，但当祖先元素具有transform属性且不为none时，就会**相对于祖先元素**指定坐标，而不是浏览器窗口。常见于**导航栏**.
  * 参照物：窗口
* **inherit**（继承）：会继承父元素的position的值
  * 参照物：无
* **sticky**:**粘性定位**，基本上，可以看出是`position:relative`和`position:fixed`的结合体.
  * 注意：须指定 [`top`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/top), [`right`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/right), [`bottom`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/bottom) 或 [`left`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/left) 四个阈值其中之一，才可使粘性定位生效。否则其行为与相对定位相同。
  * 参照物：
  * 


​	







### sticky

#### 定义

粘性定位可以被认为是相对定位和固定定位的混合。



#### 深入

在没有超过阈值时，可以看作相对定位。

例子

```html
<div class=“father”>
    活动范围
  <div class=“son”>
     儿子 
      </div>
</div>
```

```css
div {
    height: 100px;    
    margin-top: 50px;
    border: solid deepskyblue;
}
nav {
    position: sticky;
    top: 20px; 
    background: lightskyblue;
}
```

父元素的` height: 100px;    `就是所说的阈值，也就是子元素的活动区域，超过这个范围就会消失也窗口的固定位置。



子元素的`top：20px` 这是一定要设置的，不设置会无法生效，只能当作相对定位使用.









参考： [MDN position](https://developer.mozilla.org/zh-CN/docs/Web/CSS/position)

​	[深入理解position sticky粘性定位的计算规则](https://www.zhangxinxu.com/wordpress/2020/03/position-sticky-rules/)

​	[杀了个回马枪，还是说说position:sticky吧](https://www.zhangxinxu.com/wordpress/2018/12/css-position-sticky/)

