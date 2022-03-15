### 类数组 （伪数组）

函数中的隐含参数，和数组操作方式基本一致，**但是无法使用数组的原型方法**

<br>


```javascript
function sum(){
    let sum = 0;
    for(let i = 0;i<arguments.length;i++){
        sum += arguments[i];
    }
    return sum;
    }

console.log(sum(1,2,3)); //6
        
```