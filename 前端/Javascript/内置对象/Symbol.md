### Symbol 类型

对象的**属性键**只能是字符串类型或者 Symbol 类型

<br>


“Symbol” 值表示唯一的标识符

```javascript
// 给 Symbol 一个描述（也称为 Symbol 名），这在代码调试时非常有用
let id1 = Symbol("id");
let id2 = Symbol("id");

alert(id1 == id2); // false
```

<br>

**Symbol 不会被自动转换为字符串**

```javascript
let id = Symbol("id");
alert(id); // 类型错误：无法将 Symbol 值转换为字符串。

let id = Symbol("id");
alert(id.toString()); // Symbol(id)，现在它有效了



let id = Symbol("idName");
alert(id.description); // idName
```


<br>

<br>

### 对象中的Symbol

```javascript
let person = {
    name: "John",
    [id]:12345
};

console.log(person[id]);
```

<br>

**Symbol 允许我们创建对象的“隐藏”属性，Symbol 属性不会被意外访问到，第三方代码根本不会看到**

<br>

**“隐藏符号属性”原则:**

- 如果另一个脚本或库遍历我们的对象，它不会意外地访问到符号属性
- Symbol 在 for…in 中会被跳过
- Object.keys(user) 也会忽略它们
- **但是! Object.assign 会同时复制字符串和 symbol 属性**

<br>

<br>

### 全局 symbol

所有的 Symbol 都是不同的，即使它们有相同的名字。但有时我们想要名字相同的 Symbol 具有相同的实体


```javascript
// 从全局注册表中读取
let id = Symbol.for("id"); // 如果该 Symbol 不存在，则创建它

// 再次读取（可能是在代码中的另一个位置）
let idAgain = Symbol.for("id");

// 相同的 Symbol
alert( id === idAgain ); // true
```

<br>

<br>

### Symbol.keyFor

Symbol.keyFor 内部使用全局 Symbol 注册表来查找 Symbol 的键。所以它不适用于非全局 Symbol

<br>

```javascript
// 通过 Symbol 获取 name
alert( Symbol.keyFor(sym) ); // name
alert( Symbol.keyFor(sym2) ); // id




let globalSymbol = Symbol.for("name");
let localSymbol = Symbol("name");

alert( Symbol.keyFor(globalSymbol) ); // name，全局 Symbol
alert( Symbol.keyFor(localSymbol) ); // undefined，非全局

alert( localSymbol.description ); // name
```