dan在说明中强调了
>**函数式组件捕获了渲染所用的值。（Function components capture the rendered values.）**

指出最大的区别在于this的使用，this具有时效性，在处理异步时，会获取最新值输出



function

```jsx
function Clock(props) {
  return (
    <div>      <h1>Hello, world!</h1>      <h2>It is {props.date.toLocaleTimeString()}.</h2>    </div>  );
}
```



class

```jsx
class Clock extends React.Component {
  render() {
    return (
      <div>
        <h1>Hello, world!</h1>
        <h2>It is {this.props.date.toLocaleTimeString()}.</h2>
      </div>
    );
  }
}
```












[how-are-function-components-different-from-classes](https://overreacted.io/zh-hans/how-are-function-components-different-from-classes/)