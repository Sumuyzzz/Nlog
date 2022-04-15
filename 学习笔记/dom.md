优先使用querySelector和querySelectorAll

要兼容IE才用getElement(s)ByXXX

在div放入页面之前

你对div所有的操作都属于JS线程内的操作

把div放入页面之时

浏览器会发现JS的意图

就会通知渲染线程在页面中渲染div对应的元素

把div放入页面之后

你对div的操作都有可能回重新渲染

