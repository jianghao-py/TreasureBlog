### 什么是CSS （层叠样式表）

CSS 是一种描述 HTML 文档样式的语言，描述了如何在屏幕、纸张或其他媒体上显示 HTML 元素

<br>

<br>

### 添加 CSS

- 外部 CSS （支持不同页面复用，支持浏览器的缓存机制，从而加快网页的加载速度）

<br>

```html
<head>
<link rel="stylesheet" type="text/css" href="mystyle.css">
</head>
```

- 内部 CSS （不能跨页面，只支持本页面）

<br>

```html
<head>
<style>
body {
  background-color: linen;
}

h1 {
  color: maroon;
  margin-left: 40px;
} 
</style>
</head>
```

- 行内 CSS

<br>

```html
<body>

<h1 style="color:blue;text-align:center;">This is a heading</h1>
<p style="color:red;">This is a paragraph.</p>

</body>
```

