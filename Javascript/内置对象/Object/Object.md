### Object.assign

- Object.assign() 方法用于将所有可枚举自有 Property 的值从一个或多个源对象拷贝到目标对象
- 如果目标对象中的属性具有相同的键，则属性将被源对象中的属性覆盖
- Object.assign 方法只会拷贝源对象自身的并且可枚举的属性到目标对象

<br>

```javascript
const a = { a: 1 };
const b = Object.assign({}, a);
console.log(b); // { a: 1 }



// 如果目标对象与源对象有同名属性，或多个源对象有同名属性，则后面的属性会覆盖前面的属性
const target = { a: 1, b: 1 };

const source1 = { b: 2, c: 2 };
const source2 = { c: 3 };

Object.assign(target, source1, source2);
target // {a:1, b:2, c:3}
```


<br>

<br>

### Object.defineProperties

```javascript
const abc = { a: 1, b: 2, c: 3 };

Object.defineProperties(abc, {
  a: {
    value: 'One',
    writable: false,
    enumerable: false,
    configurable: false,
  },
  e: {
    value: 4,
  },
  f: {
    value: 5,
  },
});

console.log(abc);
// b: 2
// c: 3
// a: "One"
// e: 4
// f: 5

abc.a = 10;

console.log(abc.a);
// 'One'
```


<br>

<br>


### Object.defineProperty


```javascript
const foo = {};

Object.defineProperty(foo, 'a', {
    value: 100,
    writable: true,
    enumerable: true,
    configurable: true
})

console.log(foo);
// { a: 100 }

const bar;

// 添加属性和存取描述符
Object.defineProperty(foo, 'b', {
    get: function(){
        return foo
    },
    set: function(newValue){
        bar = newValue
    },
    enumerable: true,
    configurable: true,
})

foo.b = 99;

console.log(foo.b);
// 99
```



<br>

<br>

### Object.entries

Object.entries() 方法用于枚举指定对象并返回以键值对组成的数组为元素的二维数组

<br>

```javascript
const a = { foo: 1, bar: 2 };
Object.entries(a);
// [['foo', 1], ['bar', 2]]

Object.entries('foo');
// [ ['0', 'f'], ['1', 'o'], ['2', 'o'] ]
```


<br>

<br>

### Object.keys

Object.keys() 方法用于获取指定对象自身可枚举 Property 组成的键名数组

```javascript
const foo = ['a', 'b', 'c'];

console.log(Object.keys(foo));
// console: ['0', '1', '2']



const foo = { 0: 'a', 1: 'b', 2: 'c' };

console.log(Object.keys(foo));
// console: ['0', '1', '2']
```

<br>

<br>

### Object.values

Object.values() 方法用于指定对象自身的所有可枚举 Property 值的数组

```javascript
const foo = { a: '1', b: '2', c: '3' };

console.log(Object.values(foo));
// ['1', '2', '3']
```