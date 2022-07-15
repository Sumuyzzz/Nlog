1. 使用input实现
原理：根据选中状态，通过：checked伪类来绑定新样式，


```html
<div class="bar">
  <input type="radio" name="my-input" id="yes" >
  <label for="yes"> </label>
  <input type="radio" name="my-input" id="no" checked>
  <label for="no"> </label>
</div>
```

```css
.bar {
  width: 80px;
  display: flex;
  border: 1px solid red;
  padding: 0;
  input {
    display: none;
    &:checked + label {
      background: #000;
    }
  }
  label {
    margin: 0;
    display: inline-block;
    width: 40px;
    height: 25px;
  }
}
```

![](https://cdn.jsdelivr.net/gh/Sumuyzzz/pictures/img/202207152247572.gif)坑位
* 表单名字要统一，也就是name要一致。



2. 