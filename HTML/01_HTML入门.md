### 什么是HTML

HTML (HyperText Markup Language) 不是一门编程语言，而是一种用来告知浏览器如何组织页面的标记语言。它由一系列的元素（elements）组成，这些元素可以用来包围不同部分的内容，使其以某种方式呈现或者工作。

<br>

### 嵌套元素

以把元素放到其它元素之中——这被称作嵌套

```html
<p>我是<strong>最</strong>强</p>
 ```

<br>

### 块级元素和内联元素（行内元素)

**行内元素**

```<span>、<em>、<a>、<input>、<img>``` 等标签是典型的行内元素

- 和其他元素在同一行上，不独占一行
- 元素的高度、宽度及顶部底部边距不可设置 (内联元素的顶部底部边距margin-top及margin-bottom属性不起作用，而margin-left及margin-right属性可以起作用。padding属性top、bottom、left、right也可起作用)
- 元素的宽度就是元素所包含的图片或文字的宽度，不可设置

**注意**：当行内元素之间有“回车”、“tab”、“空格”时就会出现间隙

**解决方案**：写在一行，中间不要有空格、回车之类的符号

<br>

**块级元素**

```<div>、<p>、<h1>...<h6>、<ol>、<ul>、<dl>、<table>、<form>``` 等标签是典型的块级元素

- 每个块状元素都从新的一行开始，并且其后的元素也另起一行（独占一行）
- 元素的高度、宽度、行高以及顶和底边距都可设置
- 元素宽度在不设置的情况下，占它本身父容器的100%（和父元素宽度一致）

<br>

**内联块级 (inline-block)**

```<img>、<input>``` 是典型的内联块级元素

- 和其他元素都在一行上
- 元素的高度、宽度、行高以及内边距和外边距都可设置

<br>

**注意**： 一般来说块级元素内可以**嵌套**块级元素和内联元素，但内联元素只能嵌套内联元素。**要注意的是**，有些特定的元素，能包含的元素也是特定的，所以具体到个别元素上，这条规律是不适用的。比如 ```<p>``` ，只能包含内联元素，而不能包含块级元素

<br>

### 空元素

在 HTML 中，在空元素上使用结束标签通常是无效的。例如，在 HTML 中，在空元素上使用结束标签通常是无效的。例如，```<input type="text"></input>``` 是无效的 HTML是无效的 HTML

常见的空元素：```<img> <link> <meta> <input>```

<br>

### 剖析HTML文档

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>我的测试站点</title>
  </head>
  <body>
    <p>这是我的页面</p>
  </body>
</html>
 ```

 - ```<!DOCTYPE html>``` : 声明文档类型，目的是要告诉标准通用标记语言解析器，它应该使用什么样的文档类型定义（DTD）来解析文档
    - **声明文档的解析类型(document.compatMode)，避免浏览器的怪异模式**
      - **BackCompat：怪异模式**，浏览器使用自己的怪异模式解析渲染页面
      - **CSS1Compat：标准模式**，浏览器使用W3C的标准解析渲染页面

    - 如果页面没有DOCTYPE的声明，那么compatMode默认就是BackCompat，浏览器按照自己的方式解析渲染页面。如果页面添加了```!DOCTYPE html>```那么，那么就等同于开启了标准模式

- ```<html></html>: <html>```元素。这个元素包裹了整个完整的页面，是一个根元素
- ```<head></head>: <head>```元素。 这个元素是一个容器，它包含了所有你想包含在HTML页面中但不想在HTML页面中显示的内容。这些内容包括你想在搜索结果中出现的关键字和页面描述，CSS样式，字符集声明等等

```html
<head>
<title>Title of the document</title>
<base href="http://www.w3school.com.cn/images/" />
<base target="_blank" />
<link rel="stylesheet" type="text/css" href="mystyle.css" />
<meta name="keywords" content="HTML, CSS, XML" />

<style type="text/css">
  body {background-color:yellow}
  p {color:blue}
</style>
</head>
 ```

- ```<meta>``` 标签提供了 HTML 文档的元数据。元数据不会显示在客户端，但是会被浏览器解析。META元素通常用于指定网页的描述，关键词，文件的最后修改时间，作者及其他元数据。

```html
<head>
<meta name="description" content="免费在线教程">
<meta name="keywords" content="HTML,CSS,XML,JavaScript">
<meta name="author" content="runoob">
<meta charset="UTF-8">
</head>
 ```

 - ```<title></title>```: 是一项元数据，用于设置页面标题，出现在浏览器标签上
 - ```<link>```： 标签定义文档与外部资源之间的关系
 - ```<base>```： 标签为页面上的所有链接规定默认地址或默认目标（target）：
 - ```<body></body>```:包含了你访问页面时所有显示在页面上的内容，文本，图片，音频，游戏等等

<br>

### 特殊字符

原义字符 | 等价字符引用 |
------ | ------ |
<   |   ```&lt;``` |
&gt;   |   ```&gt;```  |
"   |   ```&quot;```    |
'   |   ```&apos;```    |
&   |   ```&amp;``` |

<br>

### 在HTML中应用CSS和JavaScript

**CSS**

1. 外部样式表

```html
<!--  <link>元素：经常位于文档的头部。这个link元素有2个属性，rel="stylesheet"表明这是文档的样式表，而 href包含了样式表文件的路径： -->
<link rel="stylesheet" type="text/css" href="my-css-file.css">
 ```

2. 内部样式表

```html
<head>

  <style type="text/css">
    body{
      background-color: red
      }

    p{
      margin-left: 20px
      }
  </style>

</head>
 ```

 3. 内联样式

```html
<p style="color: red; margin-left: 20px">
This is a paragraph
</p>
```

<br>

**Javascript**

1. 外部引入

```html
<!-- <script>：放在文档的尾部，这样可以确保在加载脚本之前浏览器已经解析了HTML内容（如果脚本加载某个不存在的元素，浏览器会报错） -->
<script src="my-js-file.js"></script>
 ```

2. 内部嵌入

```html
<script type="text/javascript">
  alert("Hello");   
</script>
 ```

3. 行内引入

```html
<script type="text/javascript">
  <input type="button" value="Hello" onclick="alert('world')"> 
</script>
 ```







