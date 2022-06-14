### NPM

- Node Package Manager， Node包管理工具，也是一个应用程序
- Node.js的包基本遵循CommonJS规范，将一组相关模块组合在一起
- 通过NPM可以对Node工具包进行搜索、下载、安装、删除、上传


<br>


```
npm i jquery
npm i bootstrap@3.3.7


npm i xxx -S
-S  会将安装包的信息，记录在package.json中的dependencies属性（生产依赖）


npm i xxx -D
-D  会将安装包的信息，记录在package.json中的devDependencies属性 （开发依赖）


npm i xxx -g
-g  全局安装依赖，不会影响当前项目的内容，在任意位置都可以执行全局安装的依赖
npm root -g     查看全局安装目录位置
```

<br>

<br>

### 开发依赖与生产依赖

- 开发依赖：开发阶段使用的依赖，只是在开发阶段使用的包（Babel，webpack）
- 生产依赖：项目运行需要依靠的依赖（jQuery，Vue框架）


<br>

<br>

### 版本号

- ```^3.0.0```：锁定主版本，以后安装包保证3.x.x
- ```~3.1.x```：锁定小版本，以后安装包保证3.1.x
- ```3.1.1```：锁定完整版本，以后安装包保证3.1.1


<br>

<br>

### Yarn

- Facebook开源的包管理器
- 本地缓存，安装过一次的包下一次不会进行远程安装
- 并行下载，一次下载多个包
- 保证每次安装和上次是一样

<br>


```
npm install yarn -g

yarn add jquery

yarn remove jquery

yarn add babel --dev

yarn global add jquery

yarn global remove jquery

yarn list   列出已经安装过的包名
```

