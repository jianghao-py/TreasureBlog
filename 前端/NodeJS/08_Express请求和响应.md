### 请求

```javascript
const express = require('express');

const app = express();

app.get('/',(request,response)=>{
    response.send("主页面");
});

app.get('/req/:id.html',(request,response)=>{
    // 获取请求内容
    console.log(request.method);
    console.log(request.url);
    console.log(request.httpVersion);
    console.log(request.headers);

    // 获取查询字符串参数对象
    // http://127.0.0.1/req?vip=1
    // { vip: '1' }
    console.log(request.query);

    response.send("请求页面");
});


app.get("/news/:id.html",(request,reponse)=>{
    let id = request.params.id;
    console.log(id);
    reponse.send(`${id} 页面`)
});


app.listen(80,()=>{
    console.log("服务器已经启动");
});

```

<br>

<br>

### 响应

```javascript
const express = require('express');

const app = express();

app.get('/',(request,response)=>{
    response.send("主页面");
});


app.get('/res',(request,response)=>{
    response.statusCode = 200;

    response.statusMessage = "OK";

    response.setHeader("Week","Monday");

    response.download('./form.html');

    // 跳转
    response.redirect("https://www.baidu.com/");

    // 将文件中的内容响应给浏览器
    response.sendFile(__dirname+"/2-form.html");

    // response.send("响应页面");
});

app.listen(80);
```