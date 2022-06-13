## 前置准备

先打包好项目

```bash
parcel build src/index.html --no-minity --public-url ./

```

![image-20210604204044755](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210604204044755.png)

然后提交本地文件

````bash
git init 
git add .
git commit -m 'init'
````
打


![image-20210604204311855](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210604204311855.png)

```bash
git remote add origin git@github.com:username/repository.git
git branch -M master
git push -u origin master
```

![image-20210604204452215](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210604204452215.png)

关键代码

```bash
git subtree push --prefix=dist origin gh-pages
```

![image-20210604204541011](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210604204541011.png)

在设置里面找到这个

![image-20210604204600550](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210604204600550.png)

![image-20210604204631886](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210604204631886.png)

把这串文字https://sumuyzzz.github.io/fake-canvas/放到仓库的about里面就行了,或者readme.md

