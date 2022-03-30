### 不同版本的Vue

<br>

1. vue.js 和 vue.runtime.xxx.js的区别：
    - vue.js是完整版的Vue，包含：核心功能+模板解析器
    - vue.runtime.xxx.js 是运行版的Vue，包含：核心功能

<br>

2. 默认引入的vue.runtime.xxx.js没有模板解析器，不能使用template配置项，需要使用render函数接收到的createElement函数去指定具体内容

