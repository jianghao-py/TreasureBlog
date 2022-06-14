### props

<br>

- 让组件接收外部传递的数据
- props是只读的，不能修改，可以在data再接收props的值将其变成响应式
- props接收的值优先级比data内的值高

<br>

```html
<!-- App.vue -->
<template>
  <div id="app">
    <school name="polyU" address="HongKong" major="EIE" :year="2022"></school>
  </div>
</template>


<!-- School.vue -->
<template>
    <div id="school">
        <h2>{{msg}}</h2>
        <h2>学校：{{name}}</h2>
        <h2>地址：{{address}}</h2>
        <h2>专业：{{major}}</h2>
        <h2>年份：{{year}}</h2>
    </div>
</template>

<script>
export default {
    name:'SchoolName',
    data(){
        return{
            msg:"Welcome 2022",
            // this.name 来自于props
            myName:this.name  
        }
    },
    //方式一：数组式，简单声明
    props:["name","major","address"]

    //方式二：对象式，严格限制数据类型
    props:{
        name:String,
        major:String,
        address:String,
        year:Number
    }

    //方式三
    props:{
        name:{
            type:String,
            required:true
        },
        major:{
            type:String,
            required:true
        },
        address:{
            type:String,
            required:true
        },
        year:{
            type:Number,
            required:true,
            default:2022
        }
    }
}
</script>
```