### render()

<br>

```javascript
// 创建vue实例对象
new Vue({
  // 将App组件放入容器中
  render: h => h(App),
  // .$mount 等价于 el:"#app"
}).$mount('#app')


// 不简写的render
render(createElement){
    return creatElement("h1","Hello Vue");
}


// 简写的render第一步
render:createElememt => creatElement("h1","Hello Vue");
// 简写的render第二步
render: h => h("h1","Hello Vue");
// 简写的render最终，内容换成组件
render: h => h(App)
```