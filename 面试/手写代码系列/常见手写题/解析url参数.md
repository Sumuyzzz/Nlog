> 现在有如下的一个url，请你解析出GET参数


```js
let url = "http://www.xxx.com?a=1&b=2&c=3"
// 也就是获取到: {a: 1, b: 2, c: 3}

```



```js
function parse(url) {
	let url = new URLSearchParams(location.search)
    let obj = {}
    url.slice(url.indexOf('?') + 1).split('&').map(i=>{
        let[key,val] = item.split('=')
        obj[key] = val
    }
    )
    return obj
}
```