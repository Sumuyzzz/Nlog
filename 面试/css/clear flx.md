**定义**：在非ie浏览器下，容器不设置高度，子元素浮动时，父元素高度不能撑开，父元素塌陷影响布局。


### clear

如果一个元素里只有浮动元素，那它的高度会是0。如果你想要它自适应即包含所有浮动元素，那你需要清除它的子元素

```css
#container::after {
  content: "";
  display: block;
  clear: both;
}
```

共同作用：清除浮动


> 如果不需要兼容IE9以下版本，不需要clear-fix布局

## 代替方案
1. display:flex
2. display:flow-root




 

[Clearfix example](https://codepen.io/rishabhsrao/pen/nYqKXB "Clearfix example")