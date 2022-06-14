### CSS样式操作

<br>

```javascript
box.style.width = "200px";

box.style.height = "200px";

box.style.backgroundColor = "pink";
```


<br>

<br>


### 获取CSS样式 （getComputedStyle）

- 获取元素的当前样式

<br>

- 参数：
    1. 要获取样式的DOM对象
    2. 要获取样式的伪类

<br>

- 返回值：返回一个对象，对象存储了当前元素的所有样式

<br>

```javascript
let box = document.querySelector(".box");
let getStyle = getComputedStyle(box);

console.log(getStyle.height);
```