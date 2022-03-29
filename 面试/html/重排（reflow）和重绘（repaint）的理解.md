# 浏览器渲染流程

![[Pasted image 20220330051641.png]]
浏览器渲染流程如下：

1.  解析 HTML Source，生成 DOM 树。
2.  解析 CSS，生成 CSSOM 树。
3.  将 DOM 树和 CSSOM 树结合，去除不可见元素，生成渲染树( Render Tree )。
4.  Layout (布局)：根据生成的渲染树，进行布局( Layout )，得到节点的几何信息(宽度、高度和位置等)。
5.  Painting (重绘):根据渲染树以及回流得到的几何信息，将 Render Tree 的每个像素渲染到屏幕上。














参考
[# 浏览器渲染之回流重绘](https://www.zoo.team/article/browser-redraw)