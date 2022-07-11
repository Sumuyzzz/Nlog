实现兄弟组件之间的数据传递

```html
 <div id="app">

 <child content="Dell"></child>

 <child content="Lee"></child>

 </div>

```


```js
Vue.prototype.bus = new Vue()
 
 const app = new Vue({
    el: '#app',
    components: {
        'child': {
            props: {
                content: String
            },
            data() {
                return {
                    selfContent: this.content
                }
            },
            template: '<div @click="handleContent">{{selfContent}}</div>',
            methods: {
                handleContent() {
                    this.bus.$emit('change', this.selfContent);
                }
            },
            mounted() {
                this.bus.$on('change', (msg)=>{
                    this.selfContent = msg
                    console.log(msg)
                }
                )
            },
        }
    }
})


```
![](https://cdn.jsdelivr.net/gh/Sumuyzzz/pictures/img/202207101914581.gif)