### data和el的第二种写法

<br>

```html
    <div id="root">
         <h1>hello,{{name}}</h1>
    </div>

    <script>
        const v = new Vue({
            // 函数式data
            data:function(){
                return{
                    name:"Eric"
                }
            }
        });

        v.$mount("#root");
        
    </script>
```

<br>

<br>

### 为什么需要data是函数而不是对象

- 当一个组件被定义， data 必须声明为返回一个初始数据对象的函数，因为组件可能被用来创建多个实例。如果 data 仍然是一个纯粹的对象，则所有的实例将共享引用同一个数据对象。通过提供 data 函数，每次创建一个新实例后，我们能够调用 data 函数，从而返回初始数据的一个全新副本数据对象

<br>

- 主要是因为Vue组件，**组件是可复用的 Vue 实例**，一个vue组件就是一个vue实例

<br>


- vue组件为了保证每个实例上的data数据的独立性，规定了必须使用函数，而不是对象

<br>

- 对象是对于内存地址的引用，直接定义个对象的话组件之间都会使用这个对象，这样会造成组件之间数据相互影响


<br>

<br>

### 使用对象

- 小红和小明的data都引用的是同一个内存地址

<br>

```javascript
// 创建一个简单的构建函数
var MyComponent = function() {
    
}
// 原型链对象上设置data数据，为里为Object
MyComponent.prototype.data = {
  name: 'abc',
  age: 20,
}
// 创建两个实例:小明，小红
var xiaoming = new MyComponent()
var xiaohong = new MyComponent()
// 默认状态下小明和小红的年龄一样
console.log(xiaoming.data.age === xiaohong.data.age) // true
// 改变一下小明的年龄
xiaoming.data.age = 30;
// 打印下小红的年龄，发现因为改变了小明的年龄，结果造成小红的年龄也变了
console.log(xiaoming.data.age)// 30
console.log(xiaohong.data.age) // 30
```

<br>

<br>

### 使用函数

- 使用函数后，使用的是data()函数，data()函数中的this指向的是当前实例本身

<br>

```javascript
// 创建一个简单的构建函数
var MyComponent = function() {
    // ... code here
    this.data = this.data();
}
// 原型链对象上设置data数据，为里为Object
MyComponent.prototype.data = function(){
    return {
      name: 'abc',
      age: 20,
    }
};
// 创建两个实例:小明，小红
var xiaoming = new MyComponent()
var xiaohong = new MyComponent()
// 默认状态下小明和小红的年龄一样
console.log(xiaoming.data.age === xiaohong.data.age) // true
// 改变一下小明的年龄
xiaoming.data.age = 30;
// 打印下小红的年龄，发现因为必变了小明的年龄，结果造成小红的年龄也变了
console.log(xiaoming.data.age)//30
console.log(xiaohong.data.age) // 20
```