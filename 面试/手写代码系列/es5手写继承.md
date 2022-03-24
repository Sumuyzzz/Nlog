1. 原型链
思路：父类创建实例，绑定在子类原型上
本质：替换原型，根据原型链和闭包查找或修改属性
缺点：多个实例可能会篡改原型
```js
function Parent2() {
  this.name = 'parent2';
  this.arr = [1, 2, 3];
  this.method = (arg) => console.log(arg)
}
function Child2() {
  this.type = 'child2'
}
Child2.prototype = new Parent2();
var child2 = new Child2;
```

2. 构造函数
思路：在子类，使用实例调用父类构造函数，从而通过父类构造函数获取属性
本质：省去子类重复定义实例属性的操作
缺点：只能拿到私有属性，无法获取父类原型方法

```js
function Parent1() {
  this.name = 'parent1'
}
function Child1() {
  Parent1.call(this);
  this.type = 'child1'
}
```

3. 组合继承
思路：结合原型链和构造函数的特点，
本质：
缺点：实例化时，父类被构造了两次，这没有必要  
call一次，new一次

```js
function Parent3() {
  this.name = 'parent3';
  this.arr = [1, 2, 3]
}
function Child3() {
  Parent3.call(this);
  this.type = 'child3'
}
Child3.prototype = new Parent3();

```



4. 组合优化继承
思路：在组合的基础上减少new的次数
```js
function Parent4() {
  this.name = 'parent4';
  this.arr = [1, 2, 3]
}
function Child4() {
  Parent4.call(this);
  this.type = 'child4'
}
Child4.prototype = Parent4.prototype;
```

