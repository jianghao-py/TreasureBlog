# JAVA特性

 - 面向对象（OOP）
 - 健壮 （强类型机制，垃圾回收机制，异常处理）
 - 跨平台性
 - 解释型语言（JAVA，Javscirpt）编译型语言（C/C++）
 


----------


### JVM (java虚拟机)
 - JVM是一个虚拟计算机，具有指令集并使用不同的存储区域。负责执行指令，管理数据、内存、寄存器，JVM包含在JDK中
 - 对于不同平台，有不同的JVM，从而实现跨平台


----------


### JDK (Java Development Kit, Java开发工具包)

 - JDK = JRE + java开发工具 [ java,javac,javap,javadoc ]
 - 为java开发人员提供，包含了java开发工具

----------


### JRE (Java Runtime Enviroment, Java运行时环境)

 - JRE = JVM + java核心类库
 


----------

> 什么是编译

javac HelloWorld.java

 - 有了java源文件，通过编译器将其编译成JVM可以识别的字节码文件
 - 在该源文件目录下，通过javac编译工具对HelloWorld.java文件进行编译
 - 如果该程序没有错误以及错误提示，会在当前目录下出现一个HelloWorld.class文件，该文件成为字节码文件，是可以执行的java程序
 

<br>


> 什么是运行

 - 有了可执行的java程序，通过运行工具java.exe对字节码文件进行执行
 - 本质就是将.class装载到JVM执行


<br>

> 注意事项

 - 编译后，每个class，都对应一个.class文件
 - 一个源文件中最多只能出现一个public类，其他类数量不限
 - 如果源文件包含一个public类，则该文件名必须为public类名
 - main方法也可以写在非public类中

 
 
