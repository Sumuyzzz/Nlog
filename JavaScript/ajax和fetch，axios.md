ajax:AsynchronousJavascriptAndXML,也就是异步脚本和xml语言。
一种无需加载整个页面能更新部分网页的技术，通过后台与服务器进行少量数据交换，可实现异步更新。

缺点如下：
*  基于原生XHR开发，XHR本身的架构不清晰
* 配置和调用方式非常混乱，而且基于事件的异步模型不友好

fetch:ajax的替代品，
特点如下,
* 语法简洁，更加语义化
* 基于Promise实现
* 更底层，提供API丰富
* XHR




Axios:基于Promise的封装

特点如下：
* 支持抵御XSRF