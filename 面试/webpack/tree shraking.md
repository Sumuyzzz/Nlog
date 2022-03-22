含义：按需打包，也就是没用到的js不打包，减少空间


用法：
删除多余
1. 使用es Modules语法
2. 引入时，按需引入 
```js
import {xxx} form 'lodash'
```

防止删除
1. 在 package.json中配置`sideEffects`,防止删除


开启：
在`webpack config`中将`module`设置为`prodection`