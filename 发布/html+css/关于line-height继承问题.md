### 一、line-height的值
* 常规（normal）：取决于浏览器的默认值。
* 数字（number）：**无单位的数字**，数字会与当前`font-size`相乘计算，**推荐**
* 长度（length）：**拥有单位的数值**，例如：em,px,rem...
* 百分比（%）：与自身大小有关。

### 二、继承
* 如果父元素的`line-height`**有单位**，子元素继承，则会**先换算，再继承**
* 如果无单位，子元素会**直接继承这个数值**

### 三、font-size和line-height

子元素虽然都会统一继承相同`font-size`，但是会使用不同`font-family`，所以渲染出来的`line-height`也会有所不同。

### 四、leading

英语有基线（baseline）和中线(meanline)的说法，这两条线就是所谓的`x-height`。

两种说法：
1. **现代排版**：两行文本的基线之间的距离是**现代排版软件**中所说的行距（leading）
![[Pasted image 20220618152739.png]]

2. **css**: `leading = line-height - font-size`

![[Pasted image 20220618152800.png]]