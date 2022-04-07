# 介绍

[flex](https://css-tricks.com/snippets/css/a-guide-to-flexbox):弹性盒子

当你在容器里开启`display:flex`时,里面的项目就会根据flex布局来分布位置及大小.

主要思想是让容器能够改变其项目的宽度/高度（和顺序）以最好地填充可用空间（主要是为了适应所有类型的显示设备和屏幕尺寸）。

**注意：** Flexbox 布局最适合应用程序的组件和小规模布局，而[Grid](https://css-tricks.com/snippets/css/complete-guide-grid/)布局适用于较大规模的布局。

# 基础知识及术语

![A diagram explaining flexbox terminology. The size across the main axis of flexbox is called the main size, the other direction is the cross size. Those sizes have a main start, main end, cross start, and cross end.](https://css-tricks.com/wp-content/uploads/2018/11/00-basic-terminology.svg)
![flex_terms.png](https://developer.mozilla.org/files/3739/flex_terms.png)
- **主轴(main axis)**:沿着flex元素放置方向的轴,这取决于`flex-direction`属性.该轴的开始和结束被称为 **main start** 和 **main end**。
- **交叉轴（cross axis)**:是垂直于 flex 元素放置方向的轴。其方向取决于主轴方向。该轴的开始和结束被称为 **cross start** 和 **cross end**。

****

### 父元素属性

![image-20210610181144105](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210610181144105.png)

#### display

`display`定义了一个 flex 容器；内联或块取决于给定的值。它为其所有直接子级启用 flex 上下文。

语法:

```css
display:flex|inline-flex
```

****

#### flex-direction

`flex-direction` 属性指定了内部元素是如何在 flex 容器中布局的，定义了主轴的方向(正方向或反方向)。

语法:

```css
flex-direction: row(default) | row-reverse | column | column-reverse;
```

![image-20210610184408797](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210610184408797.png)

****

#### flex-wrap

`flex-wrap`指定flex元素是否换行.

语法:

```css
flex-wrap: nowrap(default) | wrap | wrap-reverse;
```

![image-20210610191951709](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210610191951709.png)

****

#### flex-flow

`flex-flow`是`flex-direction`和`flex-wrap`属性的简写，它们共同定义了 flex 容器的主轴和横轴。默认值为`row nowrap`。

语法:

```css
flex-flow: row/column nowrap/wrap/wrap-reverse;
```

****

#### justify-content

**`justify-content`**属性定义了浏览器之间，沿着周围的内容项目如何分配空间[主轴用](https://developer.mozilla.org/en-US/docs/Glossary/Main_Axis)柔性的容器，和网格容器的内联轴。

语法:

```css
justify-content: flex-start | flex-end | center | space-between | space-around | space-evenly | start | end | left | right ... + safe | unsafe;
```

![image-20210612105759034](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210612105759034.png)

- `flex-start` （默认）：项目被打包到 flex-direction 的起点。
- `flex-end`: 项目在 flex-direction 的末尾被打包。
- `start`: 物品向开始`writing-mode`方向包装。
- `end`: 物品被包装到方向的尽头`writing-mode`。
- `left`：项目被包装在容器的左边缘，除非这对 没有意义，否则`flex-direction`它的行为就像`start`。
- `right`: 物品被包装在容器的右边缘，除非这对 没有意义，否则`flex-direction`它的行为就像`end`。
- `center`：项目沿线居中
- `space-between`：物品均匀分布在行中；第一项在开始行，最后一项在结束行
- `space-around`：项目均匀分布在一行中，周围等距。请注意，视觉上的空间不相等，因为所有项目的两侧都有相等的空间。第一个项目将与容器边缘有一个单位的空间，但下一个项目之间有两个单位的空间，因为下一个项目有自己的适用间距。
- `space-evenly`：项目的分布使得任意两个项目之间的间距（以及到边缘的空间）相等。

****

#### align-items

`align-items`:纵轴项目对齐，何为纵轴，就是丨轴，但是当你使用`flex-direction:column`时，纵轴就改变了

![image-20210611142724968](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210611142724968.png)

语法

```css
align-items: stretch | flex-start | flex-end | center | baseline | first baseline | last baseline | start | end | self-start | self-end + ... safe | unsafe;
```

- `stretch` （默认）：拉伸以填充容器（仍然尊重最小宽度/最大宽度）
- `flex-start`/ `start`/ `self-start`：物品放置在交叉轴的开始。这些之间的区别是微妙的，是关于尊重`flex-direction`规则或`writing-mode`规则。
- `flex-end`/ `end`/ `self-end`：物品放置在交叉轴的端部。区别再次是微妙的，是关于尊重`flex-direction`规则与`writing-mode`规则。
- `center`: 项目以横轴为中心
- `baseline`：项目对齐，例如它们的基线对齐

****

#### align-content

`align-content`:翻译过来就是对齐内容,当横轴上有额外空间时，这会在内部对齐 flex 容器的行，类似于`justify-content`在主轴内对齐单个项目的方式。

![image-20210611141911698](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210611141911698.png)

语法

```css
align-content: flex-start | flex-end | center | space-between | space-around | space-evenly | stretch | start | end | baseline | first baseline | last baseline + ... safe | unsafe;
```

- `normal` （默认）：项目在其默认位置打包，就好像没有设置任何值一样。
- `flex-start`/ `start`：包装到容器开头的项目。（更多支持的）`flex-start`尊重`flex-direction`而`start`尊重`writing-mode`方向。
- `flex-end`/ `end`：包装到容器末端的物品。（更多支持）`flex-end`尊重`flex-direction`而结束尊重`writing-mode`方向。
- `center`: 以容器为中心的物品
- `space-between`：物品均匀分布；第一行在容器的开头，而最后一行在结尾
- `space-around`: 项目均匀分布，每行周围等距
- `space-evenly`: 物品均匀分布，周围等距
- `stretch`: 线条伸展以占用剩余空间

### 子元素属性

![image-20210611032739178](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210611032739178.png)

#### order

默认情况下，弹性项目按源顺序排列。但是，该`order`属性控制它们在 flex 容器中出现的顺序。

一般子元素`order`的默认值都为0;相当于以当前子元素为中心它的索引就是它当前的位置

语法:

```css
order:0(default)或者所有整型
```

#### flex-grow

`flex-grow`:弹性增长,相对于整体子项目,当你设置其属性值为2时,长度为基础属性的两倍,值为整数,默认为1.

如果所有项目都`flex-grow`设置为 1，则容器中的剩余空间将平均分配给所有子项。如果其中一个孩子的值为 2，则剩余空间将占用两倍于其他空间的空间（或者至少会尝试这样做）。

**负数无效。**

![image-20210611143221703](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210611143221703.png)

#### flex-shrink

`flex-shrink`:弹性收缩,和增长相反,值为整数,默认为1.

#### flex-basic

`flex-basic`:这定义了在分配剩余空间之前元素的默认大小。它可以是长度（例如 20%、5rem 等）或关键字。

![image-20210611143649400](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210611143649400.png)

#### flex

这是`flex-grow,` `flex-shrink`和`flex-basis`组合的简写。

第二个和第三个参数（`flex-shrink`和`flex-basis`）是可选的。默认为`0 1 auto`.

语法:

```css
 flex: none | [ <'flex-grow'> <'flex-shrink'>? || <'flex-basis'> ]
```

![image-20220102162143707](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220102162143707.png)



|   单值语法   |      等同      |   **备注**   |
| :----------: | :------------: | :----------: |
| flex:initial | flex: 0 1 auto | 初始值，常用 |
|    flex:0    |  flex: 0 1 0%  |  适用场景少  |
|  flex:none   | flex: 0 0 auto |     推荐     |
|    flex:1    |  flex: 1 1 0%  |     推荐     |
|  flex:auto   | flex: 1 1 auto |  适用场景少  |



#### [align-self](https://developer.mozilla.org/zh-CN/docs/Web/CSS/align-self)

![image-20210611143723806](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210611143723806.png)

语法

```css
 align-self: auto | flex-start | flex-end | center | baseline | stretch;
```



[flex间距](https://www.w3.org/html/ig/zh/wiki/Flex-spacing#flex-spacing)





