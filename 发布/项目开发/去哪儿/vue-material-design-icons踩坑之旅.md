### 介绍
可以在vue中直接注册一个Icon组件，根据名字引入使用。


### 坑

icon名字是kebab-case语法，但是组件名引入是大驼峰语法，而且路径名很长，后面我使用vite的alias配置来替换这个又臭又长的名字


文档自带的size属性不生效，绑定class也失效，后面看了icon的样式，icon嵌套了好几层span元素，控制width和height的在最里面。


