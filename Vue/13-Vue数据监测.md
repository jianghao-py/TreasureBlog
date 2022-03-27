### 模拟Vue数据监测

<br>

```html
    <script>
        let data = {
            name:"Eric",
            age: 25
        }

        const observe = new Observer(data);
       
        let vm = {};
        vm._data = data = observe;

        // 观察者
        function Observer(obj){
            // 将对象的键转为数组
            let keys = Object.keys(obj);

            keys.forEach((item)=>{
                Object.defineProperty(this,item,{
                    get(){
                        console.log(`${item} 被读取了，触发getter`);
                        return obj[item];
                    },
                    set(val){
                        console.log(`${item} 被修改了，触发setter，重新解析模板，生成虚拟DOM......`);
                        obj[item] = val;
                    }
                })
            })  
        }
    </script>
```

<br>

<br>

