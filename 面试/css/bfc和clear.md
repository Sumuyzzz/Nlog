[[css/bfc]]





[# What is a clearfix?](https://stackoverflow.com/questions/8554043/what-is-a-clearfix)


### clear
 **`clear`** [CSS](https://developer.mozilla.org/en-US/docs/Web/CSS "CSS") 属性指定一个元素是否必须移动(清除浮动后)到在它之前的浮动元素下面。


如果一个元素里只有浮动元素，那它的高度会是0。如果你想要它自适应即包含所有浮动元素，那你需要清除它的子元素

```css
#container::after {
  content: "";
  display: block;
  clear: both;
}
```

共同作用：清除浮动