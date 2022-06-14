### less简介

<br>

- css的预处理语言，语法与css基本一致，是对css语法的扩展。浏览器无法直接执行less代码，需要将less转换为css执行
- less包含一套自定义的语法以及一个解析器，用户根据这些语法定义自己的样式规则，这些规则最终会通过解析器，编译生成对应的css文件

<br>

<br>

### 变量

<br>

```less
@color:pink;
@font14:14px;
body{
    background-color:@color;
}
```

<br>

<br>

### 嵌套

<br>

```less
.outer{
    width:200px;
    height:200px;
    background-color:#333;
    .inner{
        width:100px;
        height:100px;
        background-color:yellow;
        &:hover{
            background-color:green;
        }
    }

    &::before{

    }
}
```

<br>

<br>

### 运算

<br>

```less
@border:5px + 5;
div{
    width:200px - 50;
    height:200px / 20;
    border:@border solid red;
}
```



