```java
//好习惯
@Override
//注解：让编译器在编译时去检查是不是符合***重写***的规则

```

final关键字的用法：

(1)修饰类：表示该类不能被继承；

(2)修饰方法：表示方法不能被重写；

(3)修饰变量：表示变量只能赋值一次且赋值以后值不能被修改（常量）；

```java
//按需引入某个包的类
import java.util.*;
//但时常用方法还是单个引入；
```

# 访问权限第四种#

默认权限：缺省（default）

|本类|派生内|本类和派生外||
|-|-|-|-|
|1|同包1不0|同包1不0||
|||||

```java
void fun(){
    System.out.println("");
}

public fun1(){
    fun();//直接访问基类的默认权限
    
}
//不在同一包的派生类要引用包；
import 
    public void meth(){
    	fun();//不能被访问//不同包
}

//不同class且不是继承，不是派生类
//不会继承
//所以要创建对象
new Person().fun();//这么调用

```

```java
java.lang
包含核心类：String\Math(Π)\interger\Thread
java.awt
包含了
 java.awt
包含了构成抽象窗口工具包（AWT）的类，这个包被用来构建和管理应用程序的图形用户界面。
 java.applet
包含了可执行applet 特殊行为的类。 
java.net
包含执行与网络相关的操作的类和处理接口及统一资源定位器(URLs)的类。
java.io
包含处理I/O 文件的类。 
java.util
包含为任务设置的实用程序类，如随机数发生、定义系统特性和使用与日期日历相关的函数。 

```

# 第六章抽象类和接口#

## 1.抽象类##

###抽象类的概念###

一般作为基类存在

```java
//定义抽象类u:不能·创建抽象类对象
//想使用必须·定义·派生类
public abstract class Animal{
	//成员属性
    private String name;
    //构造方法
    public Aniaml(){
        this.name = name;
    }
    //成员方法
    public void setName(String name){
        this.name = name;
    }
    //抽象类中可以定义**抽象方法
    
    
    public abstract void shout();//喊叫
    
    
    //无具体实现{}
    //没有抽象方法也行：：：作用限制创建新对象
    
}
```

定义派生类

```java
//1.
public class Cat extend Animal{
   //限制你必须shout
    @Override
    public void shout() {
        //重写基类的抽象方法
        //必须实现抽象方法***不然报错
        System.out.println("喵喵喵");
        
    }
}
```

```java
//2.
public abstract class Dog extends Animal{
    //派生类也是抽象的
    //不必实现抽象方法了
}
```



不能实例化抽象类



###抽象类的继承###

##2.接口##

```java
public interface jiekouName{
    //接口中的***常量****声明
    //接口中的***抽象方法***声明
    
    
    //不能直接new,因为有抽象方法
}
```



###接口的概念###

###接口的定义###



###接口的实现###

包名--->new---interface---->命名

//jdk8之前

接口只能定义常量和抽象方法

```java
public interface jiekouName{
    
    //接口中的***常量****声明
    //接口中的***抽象方法***声明
    private final int NUM = 100;//不可以
    public final int NUM = 100;//***只能使用public***常量
    
    public abstract void train();
    
    
    //不能直接new,因为有抽象方法
}
```

```java
public class Cat extend Animal implements Trained{
   //限制你必须shout
    @Override
    public void shout() {
        //重写基类的抽象方法
        //必须实现抽象方法***不然报错
        System.out.println("喵喵喵");
        
    }
    @Override
    public void train() {
        System.out.println("钻火圈");
    }
}
```



###接口的继承###

##3.Object类##