# grid栅格布局

Grid布局方式借鉴了平面装帧设计中的格线系统，将格线运用在屏幕上，而不再是单一的静态页面，可以称之为真正的栅格。

### 引入

1. table表格布局，通过 Dreamweaver 拖拽表格或者手写 table 标签布局

2. float浮动及position定位布局，借助元素盒模型本身的特性以及 float position 等属性等进行布局
3. flex弹性盒模型布局，革命性的突破，解决传统布局方案上的三大痛点：排列方向、对齐方式，自适应尺寸，是目前最为成熟和强大的布局方案
4. grid栅格布局，二维布局模块，具有强大的内容尺寸和定位能力，适合需要在两个维度上对齐内容的布局

### display

```css
display: grid
display: inline-grid
```

**default:**

![image-20210602135013684](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210602135013684.png)

**grid:**

![image-20210602135054172](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210602135054172.png)

inline-grid:![image-20210602135118565](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210602135118565.png)

### 显示网格

【grid-template-rows】

**默认值为none**

![image-20210602135411940](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210602135411940.png)

```css
display:grid
grid-template-rows: 60px 40px 
height:auto
```

![image-20210602135622533](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210602135622533.png)

![image-20210602141545310](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210602141545310.png)

