### HTML5

- HTML5 是最新的 HTML 标准
- HTML5 拥有新的语义、图形以及多媒体元素
- HTML5 是跨平台的，被设计为在不同类型的硬件（PC、平板、手机、电视机等等）之上运行
- 新的语义元素，比如 ```<header>, <footer>, <article>, and <section>```
- 新的表单控件，比如数字、日期、时间、日历和滑块
- 强大的图像支持（借由 ```<canvas> 和 <svg>```）
- 强大的多媒体支持（借由 ```<video>``` 和 ```<audio>```）
- 强大的新 API，比如用本地存储取代 cookie


<br>


### 为什么需要语义化?

HTML语义化就是正确的标签做正确的事情，能够便于开发者阅读和写出更优雅的代码的同时让网络爬虫很好地解析

- 有利于SEO，有利于搜索引擎爬虫更好的理解我们的网页，从而获取更多的有效信息，提升网页的权重
- 便于团队开发和维护，语义化的HTML可以让开发者更容易的看明白，从而提高团队的效率和协调能力

<img width="500" height="300" src="../image/语义化标签.png" >

<br>

<br>

<br>

1. ```<header>```：文档的头部区域
2. ```<nav>```：定义导航链接的部分
3. ```<article>```：定义独立的内容
4. ```<section>```：定义文档中的节（section、区段）。比如章节、页眉、页脚或文档中的其他部分。
5. ```<aside>```：页面主区域内容之外的内容（比如侧边栏）
6. ```<footer>```：文档的底部区域，一个页脚通常包含文档的作者，著作权信息，链接的使用条款，联系信息等
7. ```<figure>```：规定独立的流内容（图像、图表、照片、代码等等）
8. ```<figcaption>```：定义 ```<figure>``` 元素的标题,应该被置于 "figure" 元素的第一个或最后一个子元素的位置

```html
<figure>
  <img loading="lazy" src="img_pulpit.jpg" alt="The Pulpit Rock" width="304" height="228">
  <figcaption>Fig1. - The Pulpit Pock, Norway.</figcaption>
</figure>
 ```

 <br>

### HTML5 新增input type

 ```html
color
date
datetime
datetime-local
email
month
number
range
search
tel
time
url
week
 ```

<br>

### HTML5 新增input 属性

```html
autocomplete
autofocus
form
formaction
formenctype
formmethod
formnovalidate
formtarget
height 和 width
list
min 和 max
multiple
pattern (regexp)
placeholder
required
step
 ```

<br>

### HTML5 图像

- ```<canvas>```
- ```<svg>```

<br>

### 新的媒体元素

```<video>```	定义一个视频

```<source>```	定义多种媒体资源,比如 ```<video>``` 和```<audio>```

```<track>```	定义在媒体播放器文本轨迹

```<audio>``` 定义一个音频

<br>

### HTML5 新的表单元素
 

 

 

