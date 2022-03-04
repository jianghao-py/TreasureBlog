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

- ```<canvas>``` 标签定义图形，比如图表和其他图像，您必须使用脚本(Javascript)来绘制图形
- ```<svg>``` 可伸缩矢量图形，图像在放大或改变尺寸的情况下其图形质量不会有损失，HTML5 支持内联 SVG，HTML ```<svg>``` 元素是 SVG 图形的容器

<br>

**SVG的优势：**

- SVG 图像可通过文本编辑器来创建和修改
- SVG 图像可被搜索、索引、脚本化或压缩
- SVG 是可伸缩的
- SVG 图像可在任何的分辨率下被高质量地打印
- SVG 可在图像质量不下降的情况下被放大

```html
<svg xmlns="http://www.w3.org/2000/svg" version="1.1">
   <circle cx="100" cy="50" r="40" stroke="black" stroke-width="2" fill="red" />
</svg>
```

<br>

**SVG vs Canvas:**

**SVG：**

- SVG 是一种使用 XML 描述 2D 图形的语言
- SVG 基于 XML，这意味着 SVG DOM 中的每个元素都是可用的。您可以为某个元素附加 JavaScript 事件处理器
- 在 SVG 中，每个被绘制的图形均被视为对象。如果 SVG 对象的属性发生变化，那么浏览器能够自动重现图形
- 不依赖分辨率，支持事件处理器，最适合带有大型渲染区域的应用程序（比如谷歌地图），复杂度高会减慢渲染速度，不适合游戏应用

**Canvas：**

- Canvas 通过 JavaScript 来绘制 2D 图形
- Canvas 是逐像素进行渲染的
- 在 canvas 中，一旦图形被绘制完成，它就不会继续得到浏览器的关注。如果其位置发生变化，那么整个场景也需要重新绘制，包括任何或许已被图形覆盖的对象
- 依赖分辨率，不支持事件处理器，弱的文本渲染能力，能够以 .png 或 .jpg 格式保存结果图像，最适合图像密集型的游戏，其中的许多对象会被频繁重绘


<br>

### 新的媒体元素

```<video>```	定义一个视频

```<source>```	定义多种媒体资源,比如 ```<video>``` 和```<audio>```

```<track>```	定义在媒体播放器文本轨迹

```<audio>``` 定义一个音频

<br>

### HTML5 新的表单元素
 
```<datalist>``` 元素规定输入域的选项列表

 ```html
<input list="browsers">
   <datalist id="browsers">
        <option value="Internet Explorer">
        <option value="Firefox">
        <option value="Chrome">
        <option value="Opera">
        <option value="Safari">
   </datalist>
```

<br>

```<keygen>``` 元素的作用是提供一种验证用户的可靠方法。

```<keygen>```标签规定用于表单的密钥对生成器字段 

<br>

```<output>``` 元素用于不同类型的输出，比如计算或脚本输出:

 ```html
<form oninput="x.value=parseInt(a.value)+parseInt(b.value)">0
<input type="range" id="a" value="50">100 +
<input type="number" id="b" value="50">=
<output name="x" for="a b"></output>
</form>
```


<br>


### 地理位置和拖放

HTML5 Geolocation API 用于获得用户的地理位置

使用 getCurrentPosition() 方法来获得用户的位置：

```html
<script>
var x=document.getElementById("demo");
function getLocation()
  {
  if (navigator.geolocation)
    {
    navigator.geolocation.getCurrentPosition(showPosition);
    }
  else{x.innerHTML="Geolocation is not supported by this browser.";}
  }
function showPosition(position)
  {
  x.innerHTML="Latitude: " + position.coords.latitude +
  "<br />Longitude: " + position.coords.longitude;
  }
</script>
```

<br>

**拖放**

在 HTML5 中，拖放是标准的一部分，任何元素都能够拖放


<br>

### 本地存储

通过本地存储（Local Storage），web 应用程序能够在用户浏览器中对数据进行本地的存储。

在 HTML5 之前，应用程序数据只能存储在 cookie 中，包括每个服务器请求。本地存储则更安全，并且可在不影响网站性能的前提下将大量数据存储于本地。

与 cookie 不同，存储限制要大得多（至少5MB），并且信息不会被传输到服务器。

本地存储经由起源地（origin）（经由域和协议）。所有页面，从起源地，能够存储和访问相同的数据

<br>

**localStorage 对象**

localStorage 对象存储的是没有截止日期的数据。当浏览器被关闭时数据不会被删除，在下一天、周或年中，都是可用的。


**sessionStorage 对象**

sessionStorage 对象等同 localStorage 对象，不同之处在于只对一个 session 存储数据。如果用户关闭具体的浏览器标签页，数据也会被删除。

<br>

### 应用缓存

HTML5 引入了应用程序缓存（Application Cache），这意味着可对 web 应用进行缓存，并可在没有因特网连接时进行访问。

1. 离线浏览 - 用户可在应用离线时使用它们
2. 速度 - 已缓存资源加载得更快
3. 减少服务器负载 - 浏览器将只从服务器下载更新过或更改过的资源

<br>

如需启用应用程序缓存，请在文档的 ```<html>``` 标签中包含 manifest 属性：

```html
<!DOCTYPE HTML>
<html manifest="demo.appcache">
...
</html>
```


<br>

### history API

HTML5里引用了新的API，就是history.pushState和history.replaceState，就是通过这个接口做到无刷新改变页面URL的

为了解决传统ajax带来的问题，HTML5里引入了新的API，即：history.pushState, history.replaceState 可以通过pushState和replaceState接口操作浏览器历史，并且改变当前页面的URL
 

