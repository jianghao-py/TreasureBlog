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

 ### 列表

 - 无序列表

```html
<ul>
  <li>豆浆</li>
  <li>油条</li>
  <li>豆汁</li>
  <li>焦圈</li>
</ul>
 ```

- 有序列表

```html
<ol>
  <li>沿着条路走到头</li>
  <li>右转</li>
  <li>直行穿过第一个十字路口</li>
  <li>在第三个十字路口处左转</li>
  <li>继续走 300 米，学校就在你的右手边</li>
</ol>
 ```

<br>

 ### 超链接


 ```html
<a href="https://www.mozilla.org/zh-CN/" title="了解Mozilla 使命以及如何参与贡献的最佳站点。">Mozilla 主页</a>

<!-- 会在新窗口打开文档 -->
<a href="http://www.w3school.com.cn/" target="_blank">Visit W3School!</a>

<a name="tips">基本的注意事项 - 有用的提示</a>
<a href="#tips">有用的提示</a>
 ```

 **title**：当鼠标指针悬停在链接上时，标题将作为提示信息出现

 **target**: 使用 Target 属性，你可以定义被链接的文档在何处显
 示

 **name**：name 属性规定锚（anchor）的名称，当使用命名锚（named anchors）时，我们可以创建直接跳至该命名锚（比如页面中某个小节）的链接，这样使用者就无需不停地滚动页面来寻找他们需要的信息了

 ### 文档片段

 超链接除了可以链接到文档外，也可以链接到HTML文档的特定部分（被称为文档片段）

 ```html
<h2 id="Mailing_address">邮寄地址</h2>

<p>要提供意见和建议，请将信件邮寄至 <a href="contacts.html#Mailing_address">我们的地址</a>。</p>

<!-- 也可以在同一份文档下，通过链接文档片段，来链接到同一份文档的另一部分： -->
<p>本页面底部可以找到 <a href="#Mailing_address">公司邮寄地址</a>。</p>
 ```

 ### 电子邮件

 ```html
<a href="mailto:ljh1471647441@gmail.com">发送</a>
 ```
 
 <br>
 
 ### 绝对路径和相对路径

- 相对路径：以引用文件本身所在位置为参考基础，而建立出的目录路径
- 绝对路径：以根目录为参考基础的目录路径，完整路径

 

