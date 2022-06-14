### 介绍

- HTTP（hypertext transport protocol）协议也叫**超文本传输协议**

<br>

协议主要规定了两方面的内容：

1. 客户端向服务器发送数据：请求报文
2. 服务器向客户端返回数据：响应报文

<br>

<br>

### 请求报文

<br>

- 请求行
- 请求头
- 空行
- 请求体

<br>

```http
<!-- 请求行 -->
GET http://localhost:3000/index.html?username=sunwukong&password=123123 HTTP/1.1 
<!-- 请求头 -->
Host: localhost:3000
Connection: keep-alive
Pragma: no-cache
Cache-Control: no-cache
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/64.0.3282.140 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,image/apng,*/*;q=0.8
Accept-Encoding: gzip, deflate, br
Accept-Language: zh-CN,zh;q=0.9
```

<br>

每一行的解释：

1. 请求路径和HTTP协议版本
2. 请求的主机名为localhost，端口号3000
3. keep-alive：处理完这次请求后继续保持连接，默认为3000ms
4. Pragma: no-cache：不缓存该资源，http 1.0的规定
5. Cache-Control: no-cache： 不缓存该资源 http 1.1的规定，优先级更高
6. 1：告诉服务器，支持发请求的时候不用 http 而用 https
7. 浏览器信息
8. 当前客户端可以接收的文档类型。q 相当于描述了客户端对于某种媒体类型的喜好系数，该值的范围是 0-1。默认为1
9. 支持的压缩格式。数据在网络上传递时，服务器会把数据压缩后再发送
10. 当前客户端支持的语言，可以在浏览器的工具选项中找到语言相关信息


<br>

<br>

### 响应报文

<br>

- 响应行
- 响应头
- 空行
- 响应体
    - HTML
    - CSS
    - Javascript
    - JSON
    - 图片

<br>

```http
<!-- 响应行 -->
HTTP/1.1 200 OK
<!-- 响应头 -->
X-Powered-By: Express
Accept-Ranges: bytes
Cache-Control: public, max-age=0
Last-Modified: Wed, 21 Mar 2018 13:13:13 GMT
ETag: W/"a9-16248b12b64"
Content-Type: text/html; charset=UTF-8
Content-Length: 169
Date: Thu, 22 Mar 2018 12:58:41 GMT
Connection: keep-alive

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>首页</title>
</head>
<body>
  <h1>网站首页</h1>
</body>
</html>
```

<br>

每一行的解释：

1. 协议是HTTP 1.1版本，请求响应成功
2. 自定义的头，表示用的框架，一般不返回容易造成安全漏洞
3. 告诉浏览器支持多线程下载
4. 强制对所有静态资产进行缓存，即使它通常不可缓存。max-age指定多久缓存一次
5. 这个资源最后一次被修改的日期和时间
6. 请求资源的标记/ID
7. 返回响应体资源类型
8. 响应体的长度
9. 提供了日期的时间标志，标明响应报文是什么时间创建的


<br>

<br>


### GET 和 POST 区别

1. GET 主要用来获取数据, POST 主要用来提交数据
2. GET 带参数请求是将参数缀到 URL 之后, 在地址栏输入url访问网站就是 GET 请求, POST 带参数请求是将参数放到请求体中
3. POST 请求相对 GET 安全一些, 因为在浏览器中参数会暴露在地址栏
4. GET 请求大小有限制, 一般为 2k, 而 POST 请求则没有大小限制




<br>

<br>


### 响应状态码

1. 200：请求成功，浏览器会把响应体内容（通常是html）显示在浏览器中；
2. 301：重定向，被请求的旧资源永久移除了（不可以访问了），将会跳转到一个新资源，搜索引擎在抓取新内容的同时也将旧的网址替换为重定向之后的网址；
3. 302：重定向，被请求的旧资源还在（仍然可以访问），但会临时跳转到一个新资源，搜索引擎会抓取新的内容而保存旧的网址；
4. 304：（Not Modified）请求资源未被修改，浏览器将会读取缓存；
5. 403：forbidden 禁止的
6. 404：请求的资源没有找到，说明客户端错误的请求了不存在的资源；
7. 500：请求资源找到了，但服务器内部出现了错误；


