[初始代码](https://codepen.io/gaearon/pen/oWWQNa?editors=0010)
```jsx
class Square extends React.Component {
  render() {
    return (
      <button className="square">
        {/* TODO */}
      </button>
    );
  }
}
```
```jsx
class Board extends React.Component {
  renderSquare(i) {
    return <Square />;
  }

  render() {
    const status = 'Next player: X';

    return (
      <div>
        <div className="status">{status}</div>
        <div className="board-row">
          {this.renderSquare(0)}
          {this.renderSquare(1)}
          {this.renderSquare(2)}
        </div>
        <div className="board-row">
          {this.renderSquare(3)}
          {this.renderSquare(4)}
          {this.renderSquare(5)}
        </div>
        <div className="board-row">
          {this.renderSquare(6)}
          {this.renderSquare(7)}
          {this.renderSquare(8)}
        </div>
      </div>
    );
  }
}

```

```jsx
class Game extends React.Component {
  render() {
    return (
      <div className="game">
        <div className="game-board">
          <Board />
        </div>
        <div className="game-info">
          <div>{/* status */}</div>
          <ol>{/* TODO */}</ol>
        </div>
      </div>
    );
  }
}
```

通过阅读代码，你可以看到我们有三个 React 组件：

-   Square
-   Board
-   Game


props传递数据
props：一个属性的集合，用于父子组件数据通讯

```jsx
class Square extends React.Component {
  render() {
    return (
      <button className="square">
        {this.props.value}
      </button>
    );
  }
}
  renderSquare(i) {
    return <Square value={i}/>;
  }
```
      
`{this.props.value}`：因为class组件需要this访问来获取props上的value

`<Square value={i}/>`：因为i 是变量，所以需要｛｝来模拟js环境

后续代码

使用state来存储值
state：用于缓存状态，便于回退，注意**状态不可更改**

```jsx
constructor(props) {    
	super(props);    
	this.state = {      
	value: null,    
	};  
}
```
