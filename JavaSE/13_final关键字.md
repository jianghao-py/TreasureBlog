# final 关键字

final可以修饰类，属性，方法和局部变量

1. 不希望类被继承时，可以使用final修饰
2. 不希望父类的某个方法被子类重写时，可以使用final修饰
3. 不希望类的某个属性被修改时
4. 不希望某个局部变量被修改时

<br>

**细节**

final修饰符在定义变量时，必须赋初始值：

```java
class Person{
    //1.定义时
    private final String NAME = "Eric";
    //2.构造器中
    private final int AGE;
    public  Person(){
        AGE = 23;
    }
    //3.代码块中
    private final String GENDER;
    {
        GENDER = "male";
    }
}
```

<br>

**如果是静态变量**

```java
//静态属性,静态代码块或直接赋值
    private static final int grade;
    static {
        grade = 100;
    }
    private static final int salary = 20000;
```

<br>

**final不能修饰构造器**

**如果static静态属性加上final，不会导致类加载（编译器底层）**

```java
public class FinalTest {
    public static void main(String[] args) {
        System.out.println(Dog.name);//Liu
        //没有输出“Dog被加载”，证明类没有被加载导致静态代码块没有执行
    }
}

class Dog{
    public final static String name = "Liu";

    static {
        System.out.println("Dog被加载");
    }
}
```



