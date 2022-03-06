### 为什么有的编程规范要求用 void 0 代替 undefined？

 

原因：**undefined可以作为值存在**，也就是当你给一个变量赋值undefined时，那这个变量会有一个undefined的值，这是不符合要求的，**可以通过`void 0`来获取undefined**，他不属于一个undefined值。





### 字符串有最大长度吗？

**String 有最大长度是 2^53 - 1**

