

先看结果

![[element_plus响应式菜单.gif]]


开始模拟导航栏菜单

代码如下
```html
<span>
  菜单
</span>

<ul>
  <li>1</li>
  <li>2</li>
  <li>3</li>
</ul>  


```

```css

ul{
  display:block;
}

@media (max-width: 800px) { 
  ul{
    display:none;
  }
}

```


使用span模拟导航栏菜单按钮，使用ul来模拟菜单列表

css使用媒体查询来实现动画交互，默认显示，窗口小于800px时消失




![[模拟响应式菜单1.gif]]

接着下一个功能：
![[element响应式菜单2.gif]]
点击交互菜单，先使用chckbox来模拟菜单

![[模拟响应式菜单2.gif]]

代码：
```css
input:checked+ul{
	display:block
}

```
使用兄弟选择器将ul关联起来，再使用伪类来实现交互。

这时候觉得input很丑，应该使用文字或者图标来替代。

这时候用到`label`来交互了

mdn上的描述

> 你可以点击关联的标签来聚焦或者激活这个输入元素，就像直接点击输入元素一样


>`for`即和 `<label>` 元素在同一文档中的 [可关联标签的元素](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/zh-CN/docs/Web/Guide/HTML/Content_categories#Form_labelable) 的 [`id`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Global_attributes#attr-id)。

![[模拟响应式菜单3.gif]]


最后将checkbox隐藏起来

这里面有个小坑，不能用`label`包裹`input`

最终效果

![[模拟响应式菜单4.gif]]


参考

[mdn 媒体查询](https://developer.mozilla.org/zh-CN/docs/Web/CSS/Media_Queries/Using_media_queries)

[mdn label](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/label)