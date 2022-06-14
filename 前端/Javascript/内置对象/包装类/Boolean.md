### Boolean 对象

<br>

- Boolean 内置对象是一个布尔值的对象包装器，表示两个值 true 和 false
- 当作为一个**构造函数**（带有运算符 new）调用时，Boolean() 将把它的参数转换成一个布尔值，并且返回一个包含该值的 Boolean 对象
- 如果作为一个**函数**（不带有运算符 new）调用时，Boolean() 只将把它的参数转换成一个原始的布尔值，并且返回这个值


<br>

<br>

### 创建值为 false 的 Boolean 对象

```javascript
// no param
var bNoParam = Boolean();
// 0
var bZero = Boolean(0);
// null
var bNull = Boolean(null);
// ''
var bEmptyString = Boolean('');
// undefined
var bUndefined = Boolean(undefined);
// false
var bfalse = Boolean(false);
```


<br>

<br>

### 创建值为 true 的 Boolean 对象

```javascript
// true
var btrue = Boolean(true);
// string true
var btrueString = Boolean('true');
// string false
var bfalseString = Boolean('false');
// string
var bSuLin = Boolean('Su Lin');
// array
var bArrayProto = new Boolean([]);
// object
var bObjProto = new Boolean({});
```