### Promise 配合 Ajax 使用

<br>

```html
<body>
    <div>
       <button class="btn">点击发送Ajax</button>
    </div>

    <script>
        const btn = document.querySelector("button");

        btn.addEventListener("click",function(){
            const p = new Promise((resolve,reject)=>{
                const xhr = new XMLHttpRequest();

                xhr.open("GET","https://api.apiopen.top/getJoke");

                xhr.send();

                xhr.onreadystatechange = function(){
                    if(xhr.readyState === 4){
                        if(xhr.status === 200){
                            let data = JSON.parse(xhr.response)
                            resolve(data.result[0].text);
                        }else{
                            reject(xhr.status);
                        }
                    }
                }
            })

            p.then(
                value =>{
                    console.log(value);
                },
                reason =>{
                    console.log(reason);
                }
        )

        });  
    </script>
</body>
```


<br>


<br>


### Promise 封装 Ajax

<br>

```html
 <script>
        function sendAjax(url){
            const p = new Promise((resolve,reject)=>{
                const xhr = new XMLHttpRequest();

                xhr.open("GET",url);

                xhr.send();

                xhr.onreadystatechange = function(){
                    if(xhr.readyState === 4){
                        if(xhr.status === 200){
                            resolve(xhr.response);
                        }else{
                            reject(xhr.status);
                        }
                    }
                }   
            });

            p.then(
                value =>{
                    console.log(value);
                },
                reason =>{
                    console.log(reason);
                }
            )
           
        }

        sendAjax("https://api.apiopen.top/getJoke");
    </script>
```