### AJAX 请求异常处理

<br>

```javascript
// 出错回调
xhr.onerror = ()=>{
    // 处理函数
}


// 设置时间
xhr.timeout = 2000;
xhr.ontimeout = ()=>{
    // 处理函数
}


// 关闭请求
xhr.abort()
```