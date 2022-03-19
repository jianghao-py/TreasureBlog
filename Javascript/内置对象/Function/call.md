### call()

- call方法可以用来指定函数的this

<br>

- 参数：
    1. 第一个参数：改变this指向，指向第一个参数
    2. 简而言之，用call调用函数，第一个参数是谁this就指向谁
    3. 第二到N个参数：调用函数参数列表

<br>

```javascript
function Product(name, price) {
  this.name = name;
  this.price = price;
}

function Food(name, price) {
// 调用Product构造函数，但是this指向Food，所以
  Product.call(this, name, price);
  this.category = 'food';
}

function Toy(name, price) {
  Product.call(this, name, price);
  this.category = 'toy';
}

const cheese = new Food('cheese', 5);
const robot = new Toy('robot', 40);
```


<br>

```javascript
let obj = {};
function test(){
  this.name = "Eric";
}


test.call(obj);
console.log(obj.name);
```


<br>

<br>

### 实现一个call

```javascript
Function.prototype.call = function (context) {
  // context 是调用 call 的时候参数中的第一个参数

  // 先判断当前的调用方是不是一个函数
  if (typeof this !== 'function') {
    throw new TypeError(`${this}.call is not a function.`);
  }

  // 保存调用方给的参数
  const args = [...arguments].slice(1);

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