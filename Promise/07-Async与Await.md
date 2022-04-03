### async 函数

<br>

- 函数的返回值为promise对象
- promise对象的结果由async函数执行的返回值决定

<br>

```html
 <script>
        // 和 then方法返回结果一致
        async function main(){
            // 如果返回值是一个非Promise类型的数据，则返回成功的Promise对象，值为传入的值
            // return 777;

            // 如果返回的是一个Promise对象，则返回值为Promise对象的状态
            // return new Promise((resolve,reject)=>{
            //     resolve("OK");
            // });

            // 如果抛出异常，则返回为失败的结果，值为异常值
            throw "Error";
        }

        let result = main();
        console.log(result);
</script>
```

<br>

<br>

### await 表达式

<br>

1. await右侧的表达式一般为promise对象，但也可以是其他值
2. 如果表达式是promise对象，await返回的是promise成功的值
3. 如果表达式是其他值，直接将此值作为await的返回值
4. await必须写在async函数中
5. 如果await的promise失败了，就会抛出异常，通过try catch捕获处理

<br>

```html
<script>
        // 和 then方法返回结果一致
        async function main(){
            // 如果返回值是一个非Promise类型的数据，则返回成功的Promise对象，值为传入的值
            return 777;

            // 如果返回的是一个Promise对象，则返回值为Promise对象的状态
            return new Promise((resolve,reject)=>{
                resolve("OK");
            });

            // 如果抛出异常，则返回为失败的结果，值为异常值
            throw "Error";
        }

        let result = main();
        console.log(result);

        async function aWait(){
            let p = new Promise((resolve,reject)=>{
                resolve("OK");
            })

            let res = await p;
            console.log(res);

            let res2 = await 23;
            console.log(res2);       
        }
        aWait();
    </script>
```

<br>

<br>

### async 发送 ajax 请求


<br>

```html
<body>
    <button id="btn">点击获取段子</button>
    <script>
        //axios
        function sendAJAX(url){
            return new Promise((resolve, reject) => {
                const xhr = new XMLHttpRequest();
                xhr.responseType = 'json';
                xhr.open("GET", url);
                xhr.send();
                //处理结果
                xhr.onreadystatechange = function(){
                    if(xhr.readyState === 4){
                        //判断成功
                        if(xhr.status >= 200 && xhr.status < 300){
                            //成功的结果
                            resolve(xhr.response);
                        }else{
                            reject(xhr.status);
                        }
                    }
                }
            });
        }

        //段子接口地址 https://api.apiopen.top/getJoke
        let btn = document.querySelector('#btn');

        btn.addEventListener('click',async function(){
            //获取段子信息
            let duanzi = await sendAJAX('https://api.apiopen.top/getJoke');
            console.log(duanzi);
        });
    </script>
</body>
```