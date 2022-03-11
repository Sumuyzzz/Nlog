首先要知道undefined是一个标识符，所以`var undefined = xxx`是合法的。
所以当，`var yyy = undefined` 时,实际上`yyy ='xxx'`了
因为表达式 `void 0 `没有返回值,所以应该`var yyy = void 0`
