## flex青蛙小游戏

[FLEXBOX FROGGY](https://flexboxfroggy.com/#zh-cn)

- [`flex-start`](): 元素和容器的左端对齐。
- `flex-end`: 元素和容器的右端对齐。
- `center`: 元素在容器里居中。
- `space-between`:元素之间保持相等的距离。
- `space-around`:元素周围保持相等的距离。

### 第一关

![image-20210610110406105](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210610110406105.png)

整个池塘是contain-box,而青蛙是items

```css
#pond {
  display: flex;
  justify-content: flex-end;
}
```

****

### 第二关

![image-20210610200430616](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210610200430616.png)

```css
#pond {
  display: flex;
justify-content:center;
}
```



****

### 第三关

![image-20210610211153897](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210610211153897.png)

```css
#pond {
  display: flex;
 justify-content:space-around;
}
```



### 第四关

![image-20210610222215068](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210610222215068.png)

```css
#pond {
  display: flex;
justify-content:space-between;
}
```



### 第五关

![image-20210610222755704](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210610222755704.png)

```css
#pond {
  display: flex;
align-items:flex-end;
}
```



### 六

![image-20210611004024421](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210611004024421.png)

```css
#pond {
  display: flex;
justify-content:center;
align-items:center;
}
```



### 7

![image-20210611004617208](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210611004617208.png)

```css
#pond {
  display: flex;
justify-content:space-around;
align-items:flex-end
}
```



### 8

![image-20210611012038397](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210611012038397.png)

```css
#pond {
  display: flex;
flex-direction:row-reverse
}
```





### 9

![image-20210611030754631](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210611030754631.png)

```css
#pond {
  display: flex;
flex-direction:column
}
```



### 10

![image-20210611030959475](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210611030959475.png)

```css
#pond {
  display: flex;
flex-direction:row-reverse;
justify-content:flex-end;
}
```

### 11

![image-20210611031248430](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210611031248430.png)

一开始主轴为横向,当你变成纵向时,修改上下位置布局,就是修改主轴的布局,所以要使用`justify-content`

```css
#pond {
  display: flex;
flex-direction:column;
justify-content:flex-end
}
```



### 12

![image-20210611032013250](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210611032013250.png)

```css
#pond {
  display: flex;
flex-direction:column-reverse;
justify-content:space-between;
}
```

### 13

![image-20210611032457585](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210611032457585.png)

```css
#pond {
  display: flex;
justify-content:center;
flex-direction:row-reverse;
align-items:flex-end;
}
```

### 14

![image-20210611032956309](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210611032956309.png)

```css
#pond {
  display: flex;
}

.yellow {
order:1;
}

/*等同于下面的order属性*/
.red{
  order:-1;
}
```

### 15

![image-20210611034136262](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210611034136262.png)

```css
#pond {
  display: flex;
}

.red {
order:-3
}
```

### 16

![image-20210611034739431](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210611034739431.png)

```css
#pond {
  display: flex;
  align-items: flex-start;
}

.yellow {
}
```

