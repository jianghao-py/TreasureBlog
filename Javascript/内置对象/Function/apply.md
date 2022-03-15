### apply()

- call方法可以用来指定函数的this

<br>

- 参数：
    1. 第一个参数：改变this指向，指向第一个参数
    2. 简而言之，用apply调用函数，第一个参数是谁this就指向谁
    3. 第二个参数：传入参数数组

<br>

```javascript
function Product(name, price) {
  this.name = name;
  this.price = price;
}

function Food(name, price) {
// 调用Product构造函数，但是this指向Food，所以
  Product.apply(this, [name, price]);
  this.category = 'food';
}

function Toy(name, price) {
  Product.apply(this, [name, price]);
  this.category = 'toy';
}

const cheese = new Food('cheese', 5);
const robot = new Toy('robot', 40);
```

<br>

<br>

### 实现一个apply

```javascript
Function.prototype.call = function (context) {
  // context 是调用 call 的时候参数中的第一个参数

  // 先判断当前的调用方是不是一个函数
  if (typeof this !== 'function') {
    throw new TypeError('当前调用 call 方法的不是函数.');
  }

  // 保存调用方给的参数
  const args = arguments[1];

  // 确定执行方的类型，因为可以传 null 和 undefined
  context = context || window;

  // 将调用方的内容保存为执行方的一个属性，为了保证不与执行方中的 key 键名重复
  const fn = Symbol('fn');

  context[fn] = this;

  // 执行保存的函数，这个时候作用域就是在调用方的对象的作用域下执行，改变 this 的指向
  const result = context[fn](...args);

  // 执行完删除刚才新增的属性值
  delete context[fn];

  // 返回执行结果
  return result;
};
```