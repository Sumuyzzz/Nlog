

```html
<div id="container">
  <div></div>
  <div></div>
  <div></div>
  <div></div>
  <div></div>
  <div></div>
  <div></div>
  <div></div>
</div>
```





```css
#container {
  display: grid;
  grid: repeat(3, 53px) / auto-flow 51px;
    
}

#container > div {
  background-color: #8ca0ff;
  width: 50px;
  height: 50px;
}
```



![image-20210526163713490](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210526163713490.png)

上面代码使用grid布局,先是设定每个方块的大小为50px,通过grid布局设置每个cell的大小为53px,

