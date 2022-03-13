### for...in 语句

for...in 语句用于遍历数组或者对象的属性（对数组或者对象的属性进行循环操作），**迭代的是对象的属性列表，数组的索引**

<br>

```javascript
let obj = {
    name:"Eric",
    age: 23,
    gender:"Male"
}

for(key in obj){
    console.log(key + ": " + obj[key]);          
}

//name: Eric
//age: 23
//gender: Male
```

<br>

1. for...in 循环只遍历可枚举属性，循环将遍历对象本身的所有可枚举属性，以及对象从其构造函数原型中继承的属性
2. ECMAScript 对象的属性没有顺序，因此通过 for...in 循环输出的属性名的顺序是不可预测的。具体来说，所有可枚举的属性都会被返回一次，但返回的先后次序可能会因为浏览器而异
3. 不建议用for...in遍历数组
    - 原因：
    - for...in得到的 ```index``` 索引为字符串型，不能直接进行数值运算
    - 遍历顺序有可能不是按照实际数组的内部顺序
    - 使用for in会遍历数组所有的可枚举属性，包括原型

<br>

```javascript
var arr = [1,2,3]
Array.prototype.a = 123
    
for (let index in arr) {
  let res = arr[index]
  console.log(res)
}
//1 2 3 123
```


<br>

<br>

### for...of 语句

**迭代对象键对应的值，数组索引对应的元素值**，for...of遍历的只是数组内的元素，不包括原型属性和索引

<br>

1. for...of适用遍历 数 / 数组对象 / 字符串 / map / set / arguments 等拥有迭代器对象（iterator）的集合
2. 不能遍历对象，因为没有迭代器对象


<br>

- 迭代 Array

```javascript
let iterable = [10, 20, 30];

for (let value of iterable) {
  value += 1;
  console.log(value);
}
// 11
// 21
// 31
```

<br>

- 迭代 String

```javascript
let iterable = 'boo';

for (let value of iterable) {
  console.log(value);
}
// "b"
// "o"
// "o"
```

<br>

- 迭代 arguments 对象

```javascript
(function() {
  for (let argument of arguments) {
    console.log(argument);
  }
})(1, 2, 3);
```

<br>

- 迭代 DOM 集合
- 迭代 Set

```javascript
let iterable = new Set([1, 1, 2, 2, 3, 3]);

for (let value of iterable) {
  console.log(value);
}
// 1
// 2
// 3
```

<br>

- 迭代 Map

```javascript
let iterable = new Map([["a", 1], ["b", 2], ["c", 3]]);

for (let entry of iterable) {
  console.log(entry);
}
// ["a", 1]
// ["b", 2]
// ["c", 3]

for (let [key, value] of iterable) {
  console.log(value);
}
// 1
// 2
// 3
```