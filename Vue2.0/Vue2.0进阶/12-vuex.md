### Vuex

<br>

- 在Vue中实现集中式状态管理的一个Vue插件，对Vue应用中的多个组件的共享状态进行集中式的管理 （读/写），是一种组件间通信的方式，适用于任意组件间通信

<br>

> 何时使用Vuex

<br>

1. 多个组件依赖于同一状态
2. 来自不同组件的行为需要变更同一状态


<br>

<br>

<img src="../img/vuex.png">


<br>

<br>

<br>

### 组成部分

<br>

<img src="../img/vuex2.png">

<br>

<br>

<br>


<br>

<br>

<br>


1. Vue Components：Vue组件用于派遣任务到Actions
2. Actions：用于提交 mutation，而不是直接变更状态，可以包含任意异步操作（发送请求、与后端交互）
3. Mutations：是唯一更改 store 中状态的方法，且必须是同步函数
4. State：定义了应用状态的数据结构，可以在这里设置默认的初始状态
5. Getter：允许组件从 Store 中获取数据
6. Module：允许将单一的 Store 拆分为多个 store 且同时保存在单一的状态树中


<br>

<br>

### 实现

```javascript
// main.js
import Vue from 'vue'
import App from './App.vue'
import store from "./store/index"

Vue.config.productionTip = false

new Vue({
  render: h => h(App),
  store:store
}).$mount('#app')



// store.js
// 该文件用于创建vuex中的store
import Vue from "vue"
import Vuex from "vuex"

//模块化Vuex
Vue.use(Vuex);

const sumVuex = {
    namespaced:true,
    actions:{
        add:function(context,value){
            context.commit("ADD",value)
        },
        minus:function(context,value){
            context.commit("MINUS",value)
        }
    },
    mutations:{
        ADD:function(state,value){
            state.sum += value;
        },
        MINUS:function(state,value){
            state.sum -= value;
        },
        ADDTEN:function(state,value){
            state.sum += value;
        },
        MINUSTEN:function(state,value){
            state.sum -= value;
        }
    },
    state:{
        sum:0,
        school:"polyU",
        major:"EIE"
    },
    getters:{
        bigSum(state){
            return state.sum * 10;
         },
        smallSum(state){
            return parseFloat(state.sum / 10);
        }
    }
}

const personsVuex = {
    namespaced:true,
    actions:{

    },
    mutations:{
        PUSH:function(state,value){
            state.personList.push(value)
        }
    },
    state:{
        personList:[
            {id:"1",name:"Eric"}
        ]
    },
    getters:{
        
    }
}

export default new Vuex.Store({
    modules:{
        sumVuex:sumVuex,
        personsVuex:personsVuex
    }
})


// 非模块化
// 准备actions，用于响应组件中的动作
// const actions = {
//     add:function(context,value){
//         context.commit("ADD",value)
//     },
//     minus:function(context,value){
//         context.commit("MINUS",value)
//     }
// }


// // 准备mutations，用于操作数据
// const mutations = {
//     ADD:function(state,value){
//         state.sum += value;
//     },
//     MINUS:function(state,value){
//         state.sum -= value;
//     },
//     ADDTEN:function(state,value){
//         state.sum += value;
//     },
//     MINUSTEN:function(state,value){
//         state.sum -= value;
//     },
//     PUSH:function(state,value){
//         state.personList.push(value)
//     }
// }


// // 存储数据
// const state = {
//     sum:0,
//     school:"polyU",
//     major:"EIE",
//     personList:[
//         {id:"1",name:"Eric"}
//     ]
// }


// // getters，用于将state中的数据进行加工
// const getters = {
//     bigSum(state){
//         return state.sum * 10;
//     },
//     smallSum(state){
//         return parseFloat(state.sum / 10);
//     }
// }


// 使用插件
// Vue.use(Vuex);

// //创建store
// const store = new Vuex.Store({
//    actions:actions,
//    mutations:mutations,
//    state:state, 
//    getters:getters
// });



// 导出store
// export default store;
```

<br>

<br>

```html
<!-- App.vue -->
<template>
  <div id="app">
      <sum></sum>
      <persons></persons>

      <sum-module></sum-module>
      <persons-module></persons-module>
      
  </div>
</template>

<script>
import Sum from "./components/Sum"
import Persons from "./components/Persons.vue"
import SumModule from "./components/SumModule.vue"
import PersonsModule from "./components/PersonsModule.vue"


export default {
  name: 'App',
  components: {
    Sum,
    Persons,
    SumModule,
    PersonsModule

  }
}
</script>





<!-- 非模块化 -->
<!-- Person.vue -->
<template>
    <div>
        <hr>
        <h1>Persons组件</h1>
        <input type="text" placeholder="添加人员" v-model="name">
        <button @click="pushPerson">添加</button>
        <ul v-for="item in personList" :key="item.id">
            <li>{{item.name}}</li>
        </ul>
    </div>
</template>

<script>
import {mapState} from "vuex"

export default {
    name:"Person",
    data(){
        return{
            name:"",
            count:2,
        }
    },
    methods:{
        pushPerson(){
            let countStr = this.count.toString();
            this.$store.commit("PUSH",{id:countStr,name:this.name});
            this.count++;
        }
    },
    computed:{
       ...mapState(["personList"]),
    }
}
</script>



<!-- Sum.vue -->
<template>
    <div>
        <h1>Sum组件</h1>
        <!-- 完整版vuex操作 -->
        <h2>求和值为：{{$store.state.sum}}</h2>
        <!-- 利用getters加工state数据 -->
        <h2>十倍值：{{$store.getters.bigSum}}</h2>
        <!-- mapGetters操作 -->
        <h2>除以十：{{smallSum}}</h2>
        <!-- mapState操作 -->
        <h2>我将在{{school}}，学习{{major}}</h2>
        <!-- 完整版vuex操作 -->
        <button @click="add">+</button>
        <button @click="minus(1)">-</button>

        <button @click="addTen">+10</button>
        <button @click="minusTen(10)">-10</button>

        <h3>Persons组件的总人数为：{{personList.length}}</h3>

        <hr>      
    </div>
</template>

<script>
import {mapGetters, mapState,mapMutations,mapActions} from 'vuex'

export default {
    name:"Sum",
    data(){
        return{

        }
    },
    methods:{
        add(){
            this.$store.dispatch("add",1);
        },
        // 写法一
        // ...mapActions({minus:"minus"})

        // 写法二
        ...mapActions(["minus"])
        ,
        addTen(){
            this.$store.commit("ADDTEN",10);
        },
        // 借助mapMutations生成对应的方法，方法中会调用commit去联系
        // 写法一
        ...mapMutations({minusTen:"MINUSTEN"})

        // 写法二
        // ...mapMutations(["MINUSTEN"])
    },
    computed:{
        // 借助mapState生成计算属性，从state中读取数据
        // 写法一
        // ...mapState(
        //     {school:"school",major:"major"}
        // )

        // 写法二
        ...mapState(["school","major","personList"]),
        ...mapState(["personList"]),


        // 借助mapGetters生成计算属性，从getter中读取数据
        ...mapGetters(["smallSum"])
    }  
}
</script>





<!-- 模块化 -->
<!-- PersonsModule.vue -->
<template>
    <div>
        <hr>
        <h1>Persons组件</h1>
        <input type="text" placeholder="添加人员" v-model="name">
        <button @click="pushPerson">添加</button>
        <ul v-for="item in personList" :key="item.id">
            <li>{{item.name}}</li>
        </ul>
    </div>
</template>

<script>
import {mapState,mapMutations} from "vuex"

export default {
    name:"PersonsModule",
    data(){
        return{
            name:"",
            count:2,
        }
    },
    methods:{
        pushPerson(){
            let countStr = this.count.toString();
            this.$store.commit("personsVuex/PUSH",{id:countStr,name:this.name});
            this.count++;
        }
    },
    computed:{
       ...mapState("personsVuex",["personList"]),
    }
}
</script>



<!-- SumModule.vue -->
<template>
    <div>
        <h1>Sum组件</h1>
       
        <h2>求和值为：{{sum}}</h2>
       
        <h2>十倍值：{{bigSum}}</h2>
        
        <h2>除以十：{{smallSum}}</h2>
      
        <h2>我将在{{school}}，学习{{major}}</h2>
     
        <button @click="add">+</button>
        <button @click="minus(1)">-</button>

        <button @click="ADDTEN(10)">+10</button>
        <button @click="MINUSTEN(10)">-10</button>

        <h3>Persons组件的总人数为：{{personList.length}}</h3>

        <hr>
        
       
    </div>
</template>

<script>
import {mapGetters, mapState,mapMutations,mapActions} from 'vuex'

export default {
    name:"SumModule",
    data(){
        return{

        }
    },
    methods:{
        // ...mapActions("sumVuex",["add"]),
        add(){
            this.$store.dispatch("sumVuex/add",1);
        },
        ...mapActions("sumVuex",["minus"]),
        ...mapMutations("sumVuex",["MINUSTEN"]),
        ...mapMutations("sumVuex",["ADDTEN"])

        
    },
    computed:{
        ...mapState("sumVuex",["sum","school","major","personList"]),
        
        ...mapState("personsVuex",["personList"]),
        
        ...mapGetters("sumVuex",["smallSum"]),

        ...mapGetters("sumVuex",["bigSum"]),
    }
   
}
</script>
```