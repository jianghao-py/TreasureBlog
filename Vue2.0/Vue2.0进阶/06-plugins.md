### plugins （插件）

<br>

- 包含install方法的一个对象，install第一个参数为Vue构造函数

<br>

```javascript
// plugins.js

// 插件
export default {
    install(Vue){
        // Vue是Vue实例vm的构造函数
        console.log("@@@install",Vue);

        // 过滤器
        Vue.filter('uppercase', function (value) {
            if (!value) return ''
            value = value.toString()
            return value.toUpperCase()
        })

        // 自定义指令
        Vue.directive("pink",function(element,binding){
           element.style.color = "pink";
           
        })

        // 混入
        Vue.mixin({
            methods:{
                getName(){
                    alert(this.name);
                }
            }
        })
    }
}
```

<br>

```javascript
// main.js

// import Vue from 'vue'
import App from './App.vue'
// 引入插件
import Plugins from './plugins'

Vue.config.productionTip = false

// 应用插件
Vue.use(Plugins);

// 创建vue实例对象
new Vue({
  // 将App组件放入容器中
  render: h => h(App),
  // .$mount 等价于 el:"#app"
}).$mount('#app')
```