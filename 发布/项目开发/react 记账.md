## 记账页面实现计算器布局
一开始想到grid，但感觉没挑战性。
然后尝试使用flex

思路：
* 先使用ul将button放进li管理
* ul开启flex,接着button就从上往下，变成从左往右。
* 尝试着使用flex-wrap，未生效！
	* 原因：li没有写width。
	* 解决：根据设计图，一行4个，`width：25%；`
* 最后ok按钮要站两行，根据flex布局原理，如果让一个按钮单独设置宽高，其他按钮也会自动调整。
	* 解决：单独添加className,将其absolute即可，**记住**ul要设置relative。


