如果对同一个键多次赋值，后面的值将覆盖前面的值。

```js
const map = new Map();

map
.set(1, 'aaa')
.set(1, 'bbb');

map.get(1) // "bbb"
```


注意，只有对同一个对象的引用，Map 结构才将其视为同一个键。这一点要非常小心

```js
const map = new Map();

map.set(['a'], 555);
map.get(['a']) // undefined
```

