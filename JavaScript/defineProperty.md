[Object.defineProperty](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object/defineProperty)

描述:会在对象内定义或修改属性,并返回该对象.

语法:

`Object.defineProperty(obj, prop, descriptor)`

参数:

* obj:定义的对象
* prop:要定义的或修改的名称或Symbol
* descriptor:要定义或修改的属性描述符

返回值:

定义的对象

****

对象里目前存在的属性描述符有两种主要形式：*数据描述符*和*存取描述符*。

### 共享的属性描述符

**configurable**

当且仅当该属性的 `configurable` 键值为 `true` 时，该属性的描述符才能够被改变，同时该属性也能从对应的对象上被删除。

**默认为** **`false`**。

**enumerable**

当且仅当该属性的 `enumerable` 键值为 `true` 时，该属性才会出现在对象的枚举属性中。
**默认为 `false`**。



#### 数据描述符











