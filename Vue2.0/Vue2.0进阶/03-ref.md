### ref

<br>

1. ref用来给元素或子组件注册引用信息（id的替代）
2. 在原生html标签上获取的是真实DOM元素，在组件标签上是组件实例对象


<br>

```html
<template>
  <div id="app">
    <!-- ref用来给元素或子组件注册引用信息（id的替代） -->
    <h2 ref="title">{{msg}}</h2>
    <button @click="getDom">获取h2 Dom元素</button>
    <school ref="sc"></school>
    <button @click="getSchool">获取School组件</button>
  </div>
</template>

<script>
import School from './components/School.vue'

export default {
  name: 'App',
  components: {
    School:School
  },
  data(){
    return{
      msg:"欢迎"
    }
  },
  methods:{
    getDom(){
      console.log(this.$refs.title);
    },
    getSchool(){
      console.log(this.$refs);
    }
  }
}
</script>
```