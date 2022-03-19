### this

- 任何函数本质上都是通过某个对象来调用的，如果没有指定则是由window调用

<br>

### 当以函数的形式调用函数时，this指向Window

- 如果使用严格模式（Strict Mode），则不能将全局对象用于默认绑定，因此 this 会绑定到 undefined

<br>

<br>


### 当以对象方法调用函数时，this指向调用的对象


<br>

<br>



### 当以构造函数的形式调用，this是新建的对象