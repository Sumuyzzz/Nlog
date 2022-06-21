实现Switch滑动功能

思路：用`button`+`span`来模拟开关，接着使用position来切换位置





![[开关1.gif]]


然后使用`:class`动态属性来实现值的切换，

1. 给button绑定`:class="{checked:x}"`,
2. 给x一个布尔值，
3. 给button添加方法切换

效果如下

![[开关2.gif]]

当我点击按钮时，样式根据x的真假值来进行动态绑定


最后，给button添加checked的样式，将圆圈span更改位置，button背景颜色相应改变。

效果如下
![[开关3.gif]]


最后添加一点流畅的滑动效果，使用transition

但是有个坑，
