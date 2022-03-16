### 元素

<br>

```javascript
// tagName，获取元素的大写标签名
console.log(span.tagName); // SPAN




// attributes，通过 Element.attributes 获取元素节点的所有属性节点
console.log(div.attributes); //NamedNodeMap {0: class, class: class, length: 1}




// className，获取元素的 class 属性
<div class="box"></div>
console.log(div.className); // box




// classList，获取元素节点的所有 class 属性集合
<body>
  <div class="foo bar baz">Hello world!</div>

  <script type="text/javascript">
    const foo = document.querySelector('.foo');
    const classList = foo.classList;

    console.log(classList);
    // DOMTokenList(3) ["foo", "bar", "baz", value: "foo bar baz"]
  </script>
</body>




clientWidth
获取元素节点可视部分的宽度


clientHeight
获取元素节点可视部分的高度


clientLeft
获取元素节点 offsetLeft 属性值和到当前窗口左边真实值之间的距离


clientTop
获取元素节点 offsetTop 属性值和到当前窗口上边真实值之间的距离


scrollWidth
取元素节点的总宽度，包括由于溢出导致视图不可见内容


scrollHeight
获取元素节点的总高度，包括由于溢出导致视图不可见内容


scrollLeft
获取或设置元素水平滚动条到元素左边的距离


scrollTop
获取或设置元素垂直滚动条到元素顶部的距离


offsetHeight
获取元素的像素高度（包括元素垂直内边距和边框）


offsetWidth
获取元素的像素宽度（包括元素水平内边距和边框）


offsetLeft
获取元素左上角相对于父元素左边界偏移的像素值


offsetTop
获取元素左上角相对于父元素上边界偏移的像素值
```

<br>

<br>

### innerHTML 和 innerText

- innerHTML 表示标签内部的html代码，包含标签
- innerText 表示标签内部的文本内容，不包含标签


<br>

<br>


### 方法

<br>

### createAttribute




<br>

<br>

### setAttribute



<br>

<br>


### hasAttribute



<br>

<br>


### removeAttribute



<br>

<br>