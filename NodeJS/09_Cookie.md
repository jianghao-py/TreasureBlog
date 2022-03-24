### cookie （会话控制）

- HTTP协议是一个无状态的协议，无法区分多次请求是否来自同一个客户端
- cookie本质上是存储在浏览器端的文本，随着http请求自动发送给服务器
- cookie是一个头（请求头 / 响应头）
    - 服务器以响应头的形式将Cookie返回给浏览器
    - 浏览器收到以后会自动将Cookie保存
    - 浏览器再次访问服务器时，会以请求头的形式将Cookie发送
    - 服务器就可以通过检查浏览器发回的Cookie来识别不同的浏览器

<br>

<br>


### cookie 的注意点

- cookie虽然存在于浏览器端，但是电脑中不能直接查看cookie的内容
- cookie是按照域名进行分类保存的
- 发送请求时，只会携带当前域名下的cookie进行请求
- 各个浏览器对cookie的数量和大小有不同的限制，不能在cookie中保存过多的信息
- cookie是由服务器发送给浏览器，再由浏览器将cookie返回，如果cookie较大会导致速度问题


<br>

<br>


### cookie 操作

```javascript
// cookie-parser 
//1. 安装 cookie-parser
//2. 引入 cookie-parser
var cookieParser = require('cookie-parser');

//安装 express
//引入 express 包
const express = require('express');
//创建应用对象
const app = express();
//3. 设置中间件  cookie 方法中间件内部添加的
app.use(cookieParser());
//路由的设置
app.get('/', (request, response) => {
    //设置响应
    response.end('Hello Express');
});
//设置 cookie
app.get('/set-cookie', (request, response) => {
    //4. 设置 cookie 
    response.cookie('email','xiaohigh@163.com');
    //设置带有时效性的 cookie  单位是毫秒
    response.cookie('name','xiaohigh', {maxAge: 1*60*1000});
    response.send('cookie的设置');
});
//获取 cookie
app.get('/get-cookie', (request, response) => {
    //读取 cookie
    console.log(request.cookies);//这里有 s 一定要注意
    response.send('cookie 的读取');
});

//清空 cookie
app.get('/clear-cookie', (request, response) => {
    response.clearCookie('email');
    response.send('cookie 的清除');
})

//监听端口 启动服务
app.listen(80, () => {
    console.log('服务已经启动.. 端口 80 监听中....');
});
```