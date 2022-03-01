# Object类 （java.lang.Object）

类Object是类层次结构的根类。每个类都使用Object类作为根类，所有对象（包括数组）都实现了Object类的方法

### equals方法

**== 和 equals的区别**

- ==
  - 既可以判断基本数据类型，也可以判断引用数据类型
  - 如果判断的是基本数据类型，判断的是值是否相等
  - 如果判断引用类型是否相等，判断的是内存地址

- equals：是Object类的方法，只能判断引用类型
  - 默认判断地址是否相同

    ```java
    //jdk源码
    public boolean equals(Object obj){
        return (this == obj);
    }
    ```

  - 一些子类重写了equals方法，用于判断内容是否相等（比如Integer，String）

    ```java
    //jdk源码
    public boolean equals(Object obj){
        if(obj instanceof Integer){
            return value == ((Integer)obj).intValue();
        }
        return false;
    }
    ```

    <br>


### hashCode 方法

返回该对象的哈希码值，为了提高哈希表的性能，提供具有哈希结构容器的效率

- 两个引用实例如果指向的是同一个对象，则哈希值肯定相同
- 两个引用实例如果指向的不是同一个对象，则哈希值肯定不相同
- 哈希值主要是根据内存地址值计算得来的，但是**哈希值不等于内存地**址值


<br>

### toString 方法

默认返回值：全类名 + @ + 哈希值（16进制）

```java
package pers.jianghao.equals;

public class OverrideEquals {
    public static void main(String[] args) {
        Person p1 = new Person(23,"Eric");
       
        System.out.println(p1.toString());
        //pers.jianghao.equals.Person@4eec7777
    }
}
```

**源码**

```java
public String toString() {
        return getClass().getName() + "@" + Integer.toHexString(hashCode());
}
```

<br>

**toString方法可以自己重写**

<br>

### finalize 方法

当垃圾回收器确定这里没有对该对象的更多引用时，由对象的垃圾回收器调用此方法，系统自动调用。子类可以重写该方法，用于释放资源的操作

<br>

> 什么时候被回收？

当某个对象没有任何引用时，则jvm就认为这个对象为垃圾对象，就会使用垃圾回收机制来销毁该对象。在销毁对象之前，会调用 finalize 方法

