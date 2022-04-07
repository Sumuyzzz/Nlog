[[css/bfc]]

[# What is a clearfix?](https://stackoverflow.com/questions/8554043/what-is-a-clearfix)

>在理解这个之前，请先记住一句话：“float是魔鬼，会影响其他相邻元素；但是clear是小白，其只会影响自身，不会对其他相邻元素造成影响！”---来自张鑫旭
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