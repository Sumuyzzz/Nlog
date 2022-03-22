**Loaders:**

Loaders work at the individual file level _during_ or _before_ the **bundle** is generated.

**Plugins:**

Plugins work at **bundle** or **chunk** level and usually work at the _end_ of the bundle generation process. Plugins can also modify how the bundles themselves are created. Plugins have more powerful control than loaders.

![[Pasted image 20220322172539.png]]


**The effect is different**

-   Loader literally means “loader”. Webpack regards all [file](https://developpaper.com/tag/file/ "View all posts in file")s as modules, but webpack can only parse JS files. If you want to package other files, you will use loader. So the function of loader is to enable webpack to load and parse non JavaScript files.
-   Plug in is literally “plug in”. Plugin can extend the function of webpack and make it more flexible. In the life cycle of webpack, many events will be broadcast. Plugin can listen to these events and change the output results through the API provided by webpack at the right time.

**The usage is different**

-   Where is the loader module.rules In other words, it exists as the parsing rule of the module. The type is an [array](https://developpaper.com/tag/array/ "View all posts in array"), and each item is an object, which describes what type of file (test), what loader to use, and the [parameter](https://developpaper.com/tag/parameter/ "View all posts in parameter")s to use (options)
-   Plug in is configured separately in plugins. The type is array, each item is an instance of plugin, and the parameters are passed in through the constructor.

参考

[# The difference between loader and plugin](https://developpaper.com/the-difference-between-loader-and-plugin/)

[# [Webpack loaders vs plugins; what's the difference](https://stackoverflow.com/questions/37452402/webpack-loaders-vs-plugins-whats-the-difference)](https://stackoverflow.com/questions/37452402/webpack-loaders-vs-plugins-whats-the-difference)