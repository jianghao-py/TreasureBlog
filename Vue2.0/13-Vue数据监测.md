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

### Vue.set

- data中后追加的属性，Vue默认不做响应式处理
- 需要使用Vue.set 或 vm.$set
- Vue.set只能给data内的对象追加属性，不能直接给data追加一级属性！

<br>

```html
<body>
    <div id="root">
        <h2>学校：{{schoolName}}</h2>
        <h2>地址：{{schoolAddress}}</h2>
        <hr>
        <h2>学生姓名：{{student.name.stuRealName}} , 昵称：{{student.name.stuNickName}}，Vue.set添加：{{student.name.nameTwo}}</h2>
        <button  @click="addNewData">Vue.set添加</button>
        <h2>年龄：{{student.age}}</h2>

        <hr>
        <h2>朋友们</h2>
        <ul>
            <li v-for="item in friends">姓名：{{item.name}} , 年龄：{{item.age}}</li>
        </ul>
    </div>
    <script>
        new Vue({
            el:"#root",
            data(){
                return{
                    schoolName:"polyU",
                    schoolAddress:"HongKong",
                    student:{
                        name:{
                            stuRealName:"Li",
                            stuNickName:"Eric"
                        },
                        age:23
                    },
                    friends:[
                        {name:"Clare",age:25},
                        {name:"cellPhone",age:1}
                    ]   
                }
            },
            methods:{
                addNewData(){
                    // Vue.set只能给data内的对象追加属性，不能直接给data追加一级属性！
                    Vue.set(this.student.name,"nameTwo","testName");
                }
            }
        })
    </script>
</body>
```

<br>

<br>

### Vue监测数组

- data内的数组通过数组的下标添加或删除数组元素不能触发响应式函数
- 但是Vue重写了数组的七个方法，分别为：
    1. push
    2. pop
    3. shift
    4. unshift
    5. splice
    6. sort
    7. reverse

- 通过这些数组方法操作的数组元素会变成响应式，将会触发视图更新（重新解析模板，进行更新页面）

