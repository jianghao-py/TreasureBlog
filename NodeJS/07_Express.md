### Express

- Express是一个基于Node.js平台的极简、灵活的web应用开发框架，可以快速创建web和移动设备应用
- 运行在node中用来搭建服务器的模块


<br>

```javascript
const express = require('express');

const app = express();

app.get('/',(request,response)=>{
    response.end("Hi Express");
});

app.listen(80,()=>{
    console.log("服务器已经启动");
})
```

<br>

<br>

### 路由

```javascript
const express = require('express');

const app = express();

app.get('/',(request,response)=>{
    response.setHeader("Content-type","text/html;charset=utf-8");
    response.end("路由页面");
});

app.get('/admin',(request,response)=>{
    // send方法是express封装的响应方法，等用于上面的setHeader加end
    response.send("后台页面");
});


app.get('/login',(request,response)=>{
    // send方法是express封装的响应方法，等用于上面的setHeader加end
    response.send("登录页面");
});


app.post('/login',(request,response)=>{
    // send方法是express封装的响应方法，等用于上面的setHeader加end
    response.send("登录页面");
});

app.listen(80,()=>{
    console.log("服务器已经启动");
})

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <form action="http://127.0.0.1/login" method="post">
        <input type="text" name="username"> <br>
        <input type="text" name="password"> <br>
        <button>注册</button>
    </form>
</body>
</html>
```


