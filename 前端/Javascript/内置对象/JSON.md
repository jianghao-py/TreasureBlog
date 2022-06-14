### JSON

- 一种轻量级的用于存储和交换文本信息的语法，被设计用于可读的数据交换
- JSON 主要用于在服务器和 Web 应用程序之间传输数据，Web 服务和 APIs 可以使用 JSON 格式提供公用数据，还可以用于现代编程语言中

<br>

```javascript
{
    "book": [
        {
            "id":1562366,
            "price": 21.5,
            "isPromotion": true,
            "language": "Java",
            "edition": "third",
            "author": "Herbert Schildt",
        },
        {
            "id":"07",
            "language": "C++",
            "edition": "second",
            "author": "E.Balagurusamy"
        }
    ]
}
```

<br>

JSON 值允许的 JavaScript 类型：

- 数字（整数或浮点数）
- 字符串（在双引号中）
- 逻辑值（true 或 false）
- 数组（在方括号中）
- 对象（在花括号中）
- null
- **JSON 不支持 JavaScript 中的特殊值 undefined**
- JSON 对象的属性必须加双引号


<br>

<br>


### JSON.parse()

- JSON.parse() 方法用来解析 JSON 字符串，构造由字符串描述的 JavaScript 值或对象



<br>

<br>

### JSON.stringify()

- JSON.stringify() 方法是将一个 JavaScript 值（对象或者数组）转换为一个 JSON 字符串