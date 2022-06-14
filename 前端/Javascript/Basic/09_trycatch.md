### try-catch

```try...catch``` 语句包含了由一个或者多个语句组成的 try 块, 和至少一个 catch 子句或者一个 finally 子句的其中一个，或者两个兼有


<br>


<br>


### catch

catch 子句包含 try 块中抛出异常时要执行的语句。如果有在 try 块中有任何一个语句（或者从 try 块中调用的函数）抛出异常，控制立即转向 catch 子句。如果在 try 块中没有异常抛出，会跳过 catch 子句

<br>

```javascript
try {
  console.log('1: start');

  throw 'this is a error';

  console.log('2: end');
//err接收throw语句抛出的值
} catch (err) {
  console.log('3:', err);
}


// 输出顺序：
// 1：start
// 3：this is a error
 ```


<br>


<br>


### finally

finally 子句在 try 块和 catch 块之后执行但是在下一个 try 声明之前执行

**无论是否有异常抛出或着是否被捕获它总是执行**

<br>

```javascript
function fn() {
  try {
    return 1;
  } catch (err) {
    return 2;
  } finally {
    console.log(3);
  }
}

console.log(fn());
// 输出顺序：
// 3
// 1



function fn() {
  try {
    throw 'this is a error'
  } catch (err) {
    console.log(1, err)

    return 2
  } finnally {
    console.log(3)
  }
}

console.log(fn())
// 输出顺序：
// 1 this is a error
// 3
// 2

// 如果从 finally 块中返回一个值，那么这个值将会成为整个 try-catch-finally 的返回值，无论是否有 return 语句在 try 和 catch 中
```
