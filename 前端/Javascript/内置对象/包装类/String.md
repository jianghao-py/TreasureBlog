### String

- 字符串本质上是一个字符数组
- 字符串是不可变类型，方法不会影响原字符串

<br>

<br>



### 方法

<br>

**concat()**：用来连接字符串

```javascript
let str = "hello";
let result = str.concat("world"); //helloworld
```

<br>

**charAt()**：根据索引获取字符串中的字符

```javascript
let str = "hello";
let result = str.charAt(0); //h
result = str.charAt(1); //e
```

<br>

**charCodeAt()**：根据索引获取字符串中的字符编码

```javascript
let str = "hello";
let result = str.charCodeAt(1); //101
```


<br>

**indexOf()**：获取第一次出现字符的索引

如果没找到则返回 -1

```javascript
let str = "hello";

let result = str.indexOf("h"); //0
result = str.indexOf("l",2); //2
result = str.indexOf("ello");//1
```

<br>

**lastIndexOf()**：获取最后一次出现字符的索引

```javascript
let str = "hello";
let result = str.lastIndexOf("l"); //3
```

<br>

**slice()**：截取一个字符串的子串

- 参数一：开始位置索引（包含在内）
- 参数二：结束位置索引（不包含在内）

```javascript
let str = "hello";
let result = str.slice(1,4); //ell
```

<br>

**split()**：将字符串拆分为一个数组

```javascript
let str = "h,e,l,l,o";
let result = str.split(","); //["h","e","l","l","o"]


let str = "hello";
let result = str.split(""); //["h","e","l","l","o"]
```

<br>

**trim()**：去除空格

```javascript
let str = "      hello      ";
let result = str.trim(); //hello
```

<br>

**trimStart()**：去除后部（右边）空格

```javascript
let str = "      hello      l";
let result = str.trimStart(); //hello      l
```


<br>

**trimEnd()**：去除前部（左边）空格

```javascript
let str = "      hello      ";
let result = str.trimEnd(); //l      hello
```

<br>

**includes()**：用于判断一个字符串是否包含在另一个字符串中，根据情况返回 true 或 false

```javascript
var str = 'To be, or not to be, that is the question.';

console.log(str.includes('To be'));
// true

console.log(str.includes('question'));
// true

console.log(str.includes('nonexistent'));
// false

console.log(str.includes('To be', 1));
// false

console.log(str.includes('TO BE'));
// false
```

<br>

**substr()**：返回当前字符串中一个连续的片段

```javascript
var str = 'Hello world!';

// 开始索引为1，截取长度为2
str.substr(1, 2);
// 'el'

// 开始索引为 -3+10=7，截取长度为2
str.substr(-3, 2);
// 'or'

// 开始索引为 -3+10=7，截取长度为延伸至字符结尾
str.substr(-3);
// 'orld!'

// 开始索引为 1，截取长度为延伸至字符结尾
str.substr(1);
// 'Hello world!'

// 开始索引为 -20+10=-10 即 0，截取长度为2
str.substr(-20, 2);
// 'He'

// 开始索引为 20 大于字符串长度（返回空字符串），截取长度为 2
str.substr(20, 2);
// ''

// 开始索引为 0，截取长度为 -1 和 0（返回空字符串）
str.substr(0, -1);
// ''
str.substr(0, 0);
// '' l
```


<br>

**trimStart()**：去除后部（右边）空格

```javascript
let str = "      hello      l";
let result = str.trimStart(); //hello      l
```


<br>

**trimStart()**：去除后部（右边）空格

```javascript
let str = "      hello      l";
let result = str.trimStart(); //hello      l
```



<br>

**trimStart()**：去除后部（右边）空格

```javascript
let str = "      hello      l";
let result = str.trimStart(); //hello      l
```

