### Document

- Document 接口表示任何在浏览器中载入的网页，并作为网页内容的入口，也就是 DOM 树
- 向网页文档本身提供了全局操作功能，能解决如何获取页面的 URL ，如何在文档中创建一个新的元素这样的问题


<br>

<br>

### Document 属性

```javascript
// 文档类型定义 doctype
const doc = document.doctype;

console.log(doc.name); // html




// 文档字符集 characterSet
console.log(document.characterSet); // "UTF-8"




// 文档标题 title
// 设置文档标题
document.title = 'Hello world!';



//文档加载状态 raedyState
//- loading / 正在加载：文档仍在加载
//- interactive / 可交互：文档已被解析，正在加载状态结束，但是诸如图像、样式表和框架之类的子资源仍在加载
//- complete / 完成：文档和所有子资源已完成加载，表示 load 状态的事件即将被触发
switch (document.readyState) {
  case 'loading':
    // 表示文档还在加载中，即处于“正在加载”状态
    break;
  case 'interactive':
    // 文档已经结束了“正在加载”状态，DOM元素可以被访问
    // 但是图像、样式表和框架等资源依然还在加载
    const span = document.createElement('span');
    span.textContent = 'A <span> element';
    document.body.appendChild(span);
    break;
  case 'complete':
    // 页面所有内容都已被完全加载
    const cssRule = document.styleSheets[0].cssRules[0].cssText;
    console.log(`The first CSS rule is：${cssRule}`);
    break;
}
```

<br>

<br>

### Document 方法

<br>

### getElementById

- ```document.getElementById()``` 方法通过指定 HTML 元素的 id 属性获取元素引用
- 任何 HTML 元素可以有一个 ID 属性，但在文档中该值必须唯一

<br>

```javascript
<div id="app"></div>

<script type="text/javascript">
  const elem = document.getElementById('app');

  console.log(elem);
  // <div id="app"></div>
</script>
```

<br>

<br>

### getElementsByName

- ```getElementsByName()``` 方法通过指定 HTML 元素 name 属性获取元素引用的集合
- ```<div name="app"></div>```
- 一个文档中 name 属性可能不唯一（如 HTML 表单中的单选按钮通常具有相同的 name 属性），所以 getElementsByName() 方法返回的是 元素的数组（NodeList），而不是一个元素

<br>

```javascript
<div>
  <div name="app"></div>
  <div name="app"></div>
</div>

<script type="text/javascript">
  const elemList = document.getElementsByName('app');

  console.log(elemList);
  // NodeList(3) [div, div]
</script>
```

<br>

<br>


### getElementsByTagName

- ```getElementsByTagName()``` 方法通过指定 HTML 元素标签名获取元素引用的集合
- ```const elemList = document.getElementsByTagName('li');```

<br>

```javascript
<ul>
  <li>1</li>
  <li>2</li>
  <li>3</li>
</ul>

<script type="text/javascript">
  const elemList = document.getElementsByTagName('li');

  console.log(elemList);
  // HTMLCollection(3) [li, li, li]
</script>
```

<br>

<br>

### getElementsByClassName

- ```getElementsByClassName()``` 方法通过指定 HTML 子元素的类名获取元素引用的集合
- 如果要获取 2 个以上 className，可传入多个className，每个用空格分隔

<br>

```javascript
<div class="app"></div>

<script type="text/javascript">
  const elemList = document.getElementByClassName('app');

  console.log(elemList);
  // HTMLCollection(1) [div.app]
</script>
```
<br>

<br>

### querySelector

- ```querySelector()``` 方法返回文档中匹配指定 CSS 选择器的第一个元素

<br>

```javascript
<div>
  <div id="foo"></div>
  <div class="bar"></div>
</div>

<script type="text/javascript">
  const foo = document.querySelector('#foo');
  console.log(foo);
  // <div id="foo"></div>

  const bar = document.querySelector('.bar');
  console.log(bar);
  // <div class="bar"></div>

  const div = document.querySelector('div');
  // <div>
  //   <div id="foo"></div>
  //   <div class="bar"></div>
  // </div>
</script>
```

<br>

<br>


### querySelectorAll

- ```querySelectorAll()``` 方法返回与指定的选择器组匹配的文档中的元素列表（使用 深度优先 的先序遍历文档的节点）

<br>

```javascript
<div>
  <div class="app"></div>
  <div class="app"></div>
</div>

<script type="text/javascript">
  const elemList = document.querySelectorAll('.app');

  console.log(elemList);
  // NodeList(2) [div.app, div.app]
</script>
```

<br>

<br>

### createElement

- 通过 ```document.createElement``` 创建由 tagName 指定的 HTML 元素
  
<br>

```javascript
<body>
  <h1 id="theTitle" class="hightlight summer">What's happening?</h1>
</body>


let newElement = document.createElement('p');

newElement.textContent = '新创建的p元素';

document.body.appendChild(newElement);
```

<br>

<br>


### createTextNode

- 创建一个文本节点

<br>

```javascript
<body>
  <ul>
    <li></li>
  </ul>
</body>


let text = document.createTextNode('Hello');
let li = document.querySelector("li");

li.appendChild(text); //页面上出现hello
```


<br>

<br>

