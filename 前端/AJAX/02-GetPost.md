### Get 请求

<br>

```javascript
 btnG.addEventListener("click",function(){
            const xhr = new XMLHttpRequest();

            xhr.onreadystatechange = (()=>{ 
                if(xhr.readyState === 4 && xhr.status === 200){
                    console.log(xhr.response);
                }
            })

            // query参数
            xhr.open("GET","http://127.0.0.1/get?name=Eric&age=23");
            
            // params参数
            xhr.open("GET","http://127.0.0.1/getP/Eric/23");

            // 自动解析JSON
            xhr.responseType = "json";
            
            xhr.send();
})
```

<br>

<br>

### Post 请求

<br>

```javascript
btnP.addEventListener("click",function(){
            const xhr = new XMLHttpRequest();

            xhr.onreadystatechange = (()=>{
                if(xhr.readyState === 4 && xhr.status === 200){
                    console.log(xhr.response);
                }
            })

            xhr.open("POSt","http://127.0.0.1/post");
            
            xhr.setRequestHeader("Content-type","application/x-www-form-urlencoded");

            xhr.send("name=Eric&age=23");
})
```


<br>

<br>

