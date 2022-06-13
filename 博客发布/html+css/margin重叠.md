什么是margin重叠

外边距（margin）重叠，指两个或者多个盒子的相邻边界重叠在一起，形成单一边界

相邻重叠

[margin 重叠](https://codepen.io/sumuyzzz/pen/WNMKRPP)


```html
<div class="wrapper">
      <div class="box1">

      </div>
      <div class="box2">

      </div>
```

重叠计算方式
* 全部都为正值，取最大值

	```scss

	```
	![[Pasted image 20220605171505.png]]
* 一正一负，取正值减去绝对值，全为负值，取绝对值最大值
```scss

```
![[Pasted image 20220605172236.png]]



解决：
1. 开启`float`
2. 开启`absolute`
3. 父元素开启`display:flex;`



父子重叠
解决

总结


参考
[margin 重叠](https://developer.mozilla.org/zh-CN/docs/Web/CSS/CSS_Box_Model/Mastering_margin_collapsing)
[# CSS外边距(margin)重叠及防止方法](https://juejin.cn/post/6844903497045917710)