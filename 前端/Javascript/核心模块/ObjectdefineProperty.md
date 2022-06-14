### Object.defineProperty

- ```Object.defineProperty(obj, propertyName, descriptor)```

<br>

```javascript
Object.defineProperty(user, "name", {
  value: "John"
});





// 只读（user.name 不能被重新赋值）
Object.defineProperty(user, "name", {
  writable: false
});




// 不可枚举
let user = {
  name: "John",
  toString() {
    return this.name;
  }
};

Object.defineProperty(user, "toString", {
  enumerable: false
});





// 不可配置，不可配置的属性不能被删除，它的特性（attribute）不能被修改
configurable: false
```

<br>

<br>

### Object.defineProperties

<br>

```javascript
Object.defineProperties(user, {
  name: { value: "John", writable: false },
  surname: { value: "Smith", writable: false },
  // ...
});
```

<br>

<br>


### getter 和 setter


```javascript
let user = {
  name: "John",
  surname: "Smith"
};

Object.defineProperty(user, 'fullName', {
  get() {
    return `${this.name} ${this.surname}`;
  },

  set(value) {
    [this.name, this.surname] = value.split(" ");
  }
});
```