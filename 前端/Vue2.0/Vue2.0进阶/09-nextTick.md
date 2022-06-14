### $nextTick()

<br>

- 解决某些逻辑代码执行了，但是html元素还没有渲染到页面上的问题


<br>

```javascript
this.$nextTick(function(){
    this.$refs.inputDom.focus(); 
})
```

<br>

- nextTick指定的回调会在DOM节点更新后执行