先注册账户

官网:[https://www.npmjs.com/]

点击signup

然后进行注册,记得激活邮箱





接着

在终端

运行`npm login`

![image-20210528185721455](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210528185721455.png)



![image-20210528192324102](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210528192324102.png)

如果没有显示这句话,应该是没有换源,把淘宝源换成,原始源

` npm config set registry https://registry.npmjs.org/`



接着`npm publish`

![image-20210528192639460](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210528192639460.png)

我这里报了个错误,一开始没登录成功,后来换密码,换账户重新激活都没用,最后看到一句令我没想到的话,"可能是包名字重复了,有作者上传过了",我尝试这搜了名字,没想到是同一项目,艹,进入giuhub一看跟我进度差不多,妈的