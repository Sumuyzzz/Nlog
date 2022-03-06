# 介绍

CSS Grid Layout（又名“Grid”）是一个基于二维网格的布局系统,与flex不同之处在于,flex只解决一维布局,也就是伸展布局,并不能很好的用于整体布局.



## 基础知识

### display:grid

开启网格布局

应用的元素`display: grid`。它是所有网格项的直接父项。在这个例子中`container`是网格容器。

```html
<div class="container">
  <div class="item item-1"> </div>
  <div class="item item-2"> </div>
  <div class="item item-3"> </div>
</div>
```



#### Grid Line

网格线

构成网格结构的分界线。

![image-20210612110125524](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210612110125524.png)

#### Grid Track

网络轨道

两条相邻网格线之间的空间。您可以将它们视为网格的列或行。这是第二行和第三行网格线之间的网格轨道。

![image-20210612144652519](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210612144652519.png)

#### Grid Area

网格区域

由四条网格线包围的总空间。一个网格区域可以由任意数量的网格单元组成。这是行网格线 1 和 3 以及列网格线 1 和 3 之间的网格区域。

![image-20210612144759341](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210612144759341.png)

#### Grid Item

网格项

```html
<div class="container">
  <div class="item"> </div>
  <div class="item">
    <p class="sub-item"> </p>
  </div>
  <div class="item"> </div>
</div>
```

#### Grid Cell

两个相邻行和两个相邻列网格线之间的空间。它是网格的一个“单位”。这是行网格线 1 和 2 以及列网格线 2 和 3 之间的网格单元格。

![image-20210612144937562](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210612144937562.png)

****

## Grid属性

#### Grid 容器的属性

- [`display`](https://css-tricks.com/snippets/css/complete-guide-grid/#prop-display)
- [`grid-template-columns`](https://css-tricks.com/snippets/css/complete-guide-grid/#prop-grid-template-columns-rows)
- [`grid-template-rows`](https://css-tricks.com/snippets/css/complete-guide-grid/#prop-grid-template-columns-rows)
- [`grid-template-areas`](https://css-tricks.com/snippets/css/complete-guide-grid/#prop-grid-template-areas)
- [`grid-template`](https://css-tricks.com/snippets/css/complete-guide-grid/#prop-grid-template)
- [`grid-column-gap`](https://css-tricks.com/snippets/css/complete-guide-grid/#prop-grid-column-row-gap)
- [`grid-row-gap`](https://css-tricks.com/snippets/css/complete-guide-grid/#prop-grid-column-row-gap)
- [`grid-gap`](https://css-tricks.com/snippets/css/complete-guide-grid/#prop-grid-gap)
- [`justify-items`](https://css-tricks.com/snippets/css/complete-guide-grid/#prop-justify-items)
- [`align-items`](https://css-tricks.com/snippets/css/complete-guide-grid/#prop-align-items)
- [`place-items`](https://css-tricks.com/snippets/css/complete-guide-grid/#prop-place-items)
- [`justify-content`](https://css-tricks.com/snippets/css/complete-guide-grid/#prop-justify-content)
- [`align-content`](https://css-tricks.com/snippets/css/complete-guide-grid/#prop-align-content)
- [`place-content`](https://css-tricks.com/snippets/css/complete-guide-grid/#prop-place-content)
- [`grid-auto-columns`](https://css-tricks.com/snippets/css/complete-guide-grid/#prop-grid-auto-columns-rows)
- [`grid-auto-rows`](https://css-tricks.com/snippets/css/complete-guide-grid/#prop-grid-auto-columns-rows)
- [`grid-auto-flow`](https://css-tricks.com/snippets/css/complete-guide-grid/#prop-grid-auto-flow)
- [`grid`](https://css-tricks.com/snippets/css/complete-guide-grid/#prop-grid)

#### 网格项目的属性

- [`grid-column-start`](https://css-tricks.com/snippets/css/complete-guide-grid/#prop-grid-column-row-start-end)
- [`grid-column-end`](https://css-tricks.com/snippets/css/complete-guide-grid/#prop-grid-column-row-start-end)
- [`grid-row-start`](https://css-tricks.com/snippets/css/complete-guide-grid/#prop-grid-column-row-start-end)
- [`grid-row-end`](https://css-tricks.com/snippets/css/complete-guide-grid/#prop-grid-column-row-start-end)
- [`grid-column`](https://css-tricks.com/snippets/css/complete-guide-grid/#prop-grid-column-row)
- [`grid-row`](https://css-tricks.com/snippets/css/complete-guide-grid/#prop-grid-column-row)
- [`grid-area`](https://css-tricks.com/snippets/css/complete-guide-grid/#prop-grid-area)
- [`justify-self`](https://css-tricks.com/snippets/css/complete-guide-grid/#prop-justify-self)
- [`align-self`](https://css-tricks.com/snippets/css/complete-guide-grid/#prop-align-self)
- [`place-self`](https://css-tricks.com/snippets/css/complete-guide-grid/#prop-place-self)

## 父元素

语法

```css
display: grid | inline-grid;
```

