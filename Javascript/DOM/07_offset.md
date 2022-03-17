### clientWidth，clientHeight

- 用来获取盒子内部的大小（包括内边距和内容区）
- 值可以直接计算，不带px
- 只可读，不可改

<br>

```javascript
console.log(div.clientWidth);
console.log(div.clientHeight);
```

<br>

<br>



### offsetWidth，offsetHeight

- 用来获取盒子可见框的大小（包括内容区，内边距和边框）
- 值可以直接计算，不带px
- 只可读，不可改

<br>

```javascript
console.log(div.offsetWidth);
console.log(div.offsetHeight);
```


<br>

<br>



### offsetParent

- 获取当前元素有定位的祖先元素
- 如果没有开启定位则返回body


<br>

```javascript
console.log(div.offsetParent);
```



<br>

<br>



### offsetLeft，offsetTop

- offsetLeft：获取当前元素对于其定位元素（offsetParent）的左侧偏移量
- offsetTop：获取当前元素对于其定位元素（offsetParent）的顶部偏移量

<br>

```javascript
console.log(div.offsetTop);
console.log(div.offsetLeft);
```

<br>

<br>


### scrollHeight，scrollWidth

- 获取滚动区的大小

<br>

```javascript
console.log(div.scrollHeight);
console.log(div.scrollWidth);
```

<br>

<br>


### scrollTop，scrollLeft

- 获取滚动条的偏移量，滚动条的滚动距离
- 可读可修改
- scrollHeight - scrollTop === clientHeight，则表示滚动条到底了

<br>

```javascript
console.log(div.scrollTop);
console.log(div.scrollLeft);
div.scrollTop = 100;
```

<br>

<br>


### 鼠标X轴和Y轴

- clientX
- clientY


<br>

```javascript
area.onmousemove = function(event){
    let x = event.clientX;
    let y = event.clientY;
}
```

