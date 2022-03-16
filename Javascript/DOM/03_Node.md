### 节点 （Node）


<br>

```javascript
// Node.nodeName，获取当前节点的名称
const list = document.getElementById('list');
const item = list.firstElementChild;

console.log(list.nodeName); // ‘UL’
console.log(item.nodeName); // ‘LI’




// Node.textContent，获取或设置当前节点及其所有后代节点的文本内容
<div class="app">Hello world!</div>
<script>
  const app = document.getElementById('app');
  const text = app.textContent;
  console.log(text); // 'Hello world!'

  app.textContent = 12345;
  console.log(text); // 12345
</script>




// Node.paretnNode，获取节点的父节点（Node）
const foo = document.querySelector('.foo');

console.log(foo.parentNode); // <body>...</body>




// Node.parentElement，获取节点的父元素节点（Element）
const foo = document.querySelector('.foo');

console.log(foo.parentElement); // <body>...</body>




// Node.previousSibling，获取当前节点前面的第一个兄弟节点（Node）
const foo = document.querySelector('.foo');

console.log(foo.previousSibling); // #text




// Node.previousElementSibiling，获取当前节点前面的第一个兄弟元素节点（Element）
const foo = document.querySelector('.foo');

console.log(foo.previousSibling); // <div class="bar"></div>




// Node.nextSibiling，获取当前节点后面的第一个兄弟节点（Node）




// Node.nextElementSibiling，获取当前节点后面的第一个兄弟元素节点（Element）




// Node.firstChild，获取节点的第一个子节点（Node）
const foo = document.querySelector('.foo');

console.log(foo.firstChild); // #text




// Node.firstElementChild，获取节点的第一个子元素节点（Element）
const foo = document.querySelector('.foo');

console.log(foo.firstElementChild); // <div class="foo-1"></div>




// Node.lastChild，获取节点的最后一个子节点（Node）




// Node.lastElementChild，获取节点的最后一个元素节点（Element）




// Node.childNodes，获取节点的子节点列表（NodeList），空白文本也会包含
const foo = document.querySelector('.foo');

console.log(foo.childNodes);
// NodeList(7) [text, div.foo-1, text, div.foo-2, text, div.foo-3, text]




// Node.children，获取节点的子元素节点列表（HTMLCollection）
const foo = document.querySelector('.foo');

console.log(foo.children);
// HTMLCollection(3) [div.foo-1, div.foo-2, div.foo-3]




// Node.childElementCount，获取当前节点的所有子元素节点的数目
const foo = document.querySelector('.foo');

console.log(foo.childElementCount);
// 3
```

<br>

<br>


### 方法

```javascript
// appendChild，将指定的 childNode 参数作为最后一个子节点添加到当前节点

const foo = document.getElementById('foo');
const bar = document.getElementById('bar');

foo.appendChild(bar); 




// replaceChild，替换当前节点的某个指定子节点为指定的节点
<div id="foo">
  <div class="bar"></div>
</div>

const span = document.createElement('span');
const foo = document.getElementById('foo');
const bar = foo.firstElementChild;

foo.replace(bar, span);
// <div id="foo">
// <span></span>
// </div>




// removeChild，从 DOM 中删除一个子节点，返回删除的节点
<div id="foo">
  <div id="bar"></div>
</div>

const foo = document.getElementById('foo');
const bar = document.getElementById('bar');

foo.removeChild(bar);
// <div id="foo"></div>




// cloneNode()，克隆节点到当前节点的子节点列表（及其属性和后代节点）
<div id="foo">
  <div></div>
  <div></div>
</div>

const foo = document.getElementById('foo');

const backup = foo.cloneNode();

foo.appendChild(backup);

// <div id="foo">
//   <div></div>
//   <div></div>
//   <!-- 克隆后插入到子节点列表最后 -->
//   <div id="foo"></div>
// </div>




// hasChildNodes，判断当前节点是否含有子节点
foo.hasChildNodes




// isEqualNode，判断两个节点是否相等
items[0].isEqualNode(items[1])




// ChildNode.remove，从文档中移除当前节点
<ul class="list">
  <li class="item1"></li>
  <li class="item2"></li>
  <li class="item3"></li>
</ul>

const item1 = document.querySelector('.item1');
const item2 = document.querySelector('.item2');

item1.remove();
item2.remove();

// <ul class="list">
//   <li class="item3"></li>
// </ul>




// ChildNode.before，在其父节点的子节点列表中插入一些 Node
<ul class="list">
  <li class="item1"></li>
  <li class="item2"></li>
  <li class="item3"></li>
</ul>

const item1 = document.querySelector('.item1');
const li = document.createElement('li');
li.innerHTML = 'Hello world!';

item1.before(li);

// <ul class="list">
//   <li>Hello world!</li>
//   <li class="item1"></li>
//   <li class="item2"></li>
//   <li class="item3"></li>
// </ul>




// ChildNode.after，插入节点到当前节点后面




// ChildNode.replaceWith，替换当前节点为另一节点
const parent = document.createElement('div');
const child = document.createElment('p');

parent.appendChild(child);
const span = document.createElement('span');

child.replaceWith(span);

console.log(parent.outerHTML);
// '<div><span></span></div>'
```

