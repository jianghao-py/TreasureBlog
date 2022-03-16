### String

- 字符串本质上是一个字符数组
- 字符串是不可变类型，方法不会影响原字符串

<br>

<br>

### 属性



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