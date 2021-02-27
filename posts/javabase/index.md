# Java基础


<!--more-->



## Java基础语法





### 1. 注释、标识符、关键字

* Java的注释有三种：(单行注释，多行注释)

  ```java
  
  public class HelloWorld {
      public static void main(String[] args) {
          
          //1.单行注释
          System.out.println("Hello,World!");
  
          /*2.多行
            注释
           */
          
          
          //JavaDoc：文档注释
          /**
           * @Description  com.kinvy.base.HelloWorld
           * @Author  Kinvy
           */
      }
  }
  ```



* 标识符

  * 关键字

    ![](https://kinvy-images.oss-cn-beijing.aliyuncs.com/Images/%E5%85%B3%E9%94%AE%E5%AD%97.png)

    Java所有的组成部分都需要名字。类名、变量名以及方法名都被称为**标识符**

> 标识符的规则：以字母，$,下划线开始，不能使用关键字或保留字
>
> 基本的命名规则和C/C++一致







### 2. 数据类型

Java是强类型语言，即所有的变量必须先定义后才能使用

* Java的数据类型分为两大类

  * 基本类型

    数值类型：整数类型(`int` `shor` `byte` `long` ),浮点型(`float` `double`)  字符类型(`char` 占两个字节)

    boolean类型

  * 引用类型

    类，接口，数组

> 说明：string 是类



### 3类型转换

语法：(转换类型)变量名   

```java
public class HelloWorld {
    public static void main(String[] args) {
        char c1 = 'a';
        System.out.println(c1);
        System.out.println(int(c1));	//char-->int
    }
}

```

> 低-----------------------------------------------------------------------高
>
> byte -> short -> char -> int -> long -> flaot -> double



说明：强制转换可能存在精度丢失，自动转换（低-->高）



### 4. 常量、变量

命名规则：

* 类成员变量：首字母小写和驼峰原则：monthSalary

* 局部变量：首字母小写和驼峰原则

* 常量：大写字母和下划线：MAX_VALUE

* 类名：首字母大写和驼峰原则：Person，GoodMan

* 方法名：首字母小写和驼峰原则：run()  , startTask()

* 方法形参：下划线开始，首字母大写和驼峰原则： _Pos     `c++`

  

### 5. 运算符

Java支持的运算符：常规运算符都支持



### 6. 包机制

包语句的语法格式：  `package pkg1[. pkg2[.pkg3..]]`

导入包的语法： `import package1[.package2..].classname|*`



```java
package com.kinvy.array;	//包

import java.util.Arrays;	//导入Arrays的包

public class ArrayDemo01 {
    public static void main(String[] args) {
        int[] a = {1,2,3,4,9090,324,5412,122,3};

        System.out.println(a);
        //打印数组元素
        System.out.println(Arrays.toString((a)));

    }

}
```



说明：一般利用公司域名倒置作为包名    com.baidu.www



## Java流程控制（顺序，循环，选择）



> 参照C++流程控制语法



用户交互Scanner

```java
package com.kinvy.base;

import java.util.Scanner;

public class Demo02 {
    public static void main(String[] args) {
        //创建一个扫描器对象
        Scanner scanner = new Scanner(System.in);

        System.out.println("使用next():");

        //判断用户有没有输入字符
        if(scanner.hasNext()) {
            String str = scanner.next();
            System.out.println("输出内容为："+str);
        }
        //scanner.close();  //用完管关掉，不关会一致占用资源

        /**********************************/
         scanner = new Scanner(System.in);
        System.out.println("使用nextline():");

        if(scanner.hasNextLine()) {
            String str1 = scanner.nextLine();
            System.out.println("输出内容："+str1);
        }
        scanner.close();
	 	
        
        int i = 0;
        System.out.println("输入整数：");
        if(scanner.hasNextInt()) {
            i = scanner.nextInt();
            System.out.println("整数数据:"+i);
        } else {
            System.out.println("输入的不是整数数据！");
        }
    }
}
```





## Java方法



### 1.方法是什么

Java中的方法和C++中类的成员函数一致，用来完成特定功能的代码片段



### 2.方法的定义

```java
/*
修饰符 返回值类型  方法名（参数类型  参数名） {
	方法体
	return 返回值;
	}
*/

//方法是定义在class中的

public class Demo {
    public static void main(String[] args) {
        System.out.println("Hello,World!");

        int ret = add(10,20);	//方法调用
        System.out.println(ret);
    }
    
    //方法定义
    public static int add(int num1,int num2) {
        return num1+num2;
    }
}

```



### 3.方法的重载

方法重载的规则：

1. 方法名称必须相同
2. 参数列表必须不同（个数不同，或类型不同、参数排列顺序不同等）
3. 方法的返回类型可以相同也可以不同
4. 返回值类型不同不能作为重载的条件



```java
public class Demo {
    public static void main(String[] args) {
        System.out.println("Hello,World!");

        int ret = add(10,20);	//方法调用
        System.out.println(ret);
        
        float f = add(1.2f,1.4f);
        System.out.println(f);
    }
    
    //方法定义
    public static int add(int num1,int num2) {
        return num1+num2;
    }
    
    //重载方法
     public static float add(float num1,float num2) {
        return num1+num2;
    }
}

```





### 4. 命令行传递参数



示例：

```java
//该程序需要在命令行运行
public class Demo01 {
    public static void main(String[] args) {
        for (int i = 0; i < args.length; i++) {
            System.out.println("args["+i+"]:"+args[i]);

        }
    }
}

```



### 5.可变参数

JDK1.5开始，Java支持传递同类型的可变参数给一个方法

在方法声明中，在指定参数类型后加一个省略号(...)

一个方法中只能指定一个可变参数，它必须是方法的最后一个参数。任何普通的参数必须在它之前声明



```java
public class Demo02 {
    public static void main(String[] args) {
        Demo02 demo02 = new Demo02();
        demo02.method(12,43,54,12,56,35);
    }

    public static void method(int... number) {
        System.out.println(number);     //输出的是一个对象地址
        for (int i = 0; i < number.length; i++) {
            System.out.println(number[i]);
        }
    }
}

```



## Java OOP





### 1. 初识面向对象

 以类的形式组织代码，以对象的组织（封装）数据。

面向对象特征：封装，继承，多态





### 2. 方法

1. 定义一个 方法：

   > 修饰符  返回值类型   方法名(...) {
   > 
   > ​		方法体
   > 
   >  ​		return 返回值；
   > 
   >  }
   >
   
   示例：
   
   ```java
   public class Demo01 {
       public static void main(String[] args) {
           //int max = max(129, 12);
       }
   
       public static String sayHello() {
           return "hello";
       }
   
       public int  max(int a, int b) {
           return a>b ? a : b;
       }
   }
   ```

2. 方法的调用

   ```java
   //Demo02.java
   public class Demo02 {
       public static void main(String[] args) {
           //非静态方法实例化这个类
           Student student = new Student();
           student.speak();
   
           //静态方法  static
           Student.say();
       }
   
   }
   
   
   //Student.java  
   public class Student {
       //非静态方法
       public  void speak() {
           System.out.println("speak");
       }
   
       //静态方法
       public static   void say() {
           System.out.println("say");
       }
   }
   
   
   ```

   说明：java方法的参数传递是值传递，

### 3. 对象的创建

使用new创建对象，示例同上



* 构造器

  构造器和c++中的构造函数一致

  无参构造，有参构造，定义了有参构造，无参构造必须显示定义

  



### 4. 面向对象三大特性

* **封装：** 





* **继承：**

  Java只有单继承，没有多继承

  在java中所有的类都默认直接或间接继承Object类

  调用父类的同名属性和方法使用`super` 关键字

  ```java
  /************  Application.java  **************/
  package com.kinvy.oop;
  
  import com.kinvy.oop.demo02.Student;
  
  public class Application {
      public static void main(String[] args) {
          Student student =  new Student();
          student.test("App");
      }
  }
  
  
  /*************   Person.java   父类   **************/
  package com.kinvy.oop.demo02;
  
  //父类  Person
  public class Person {
      public Person() {
          
      }
      
      public String name = "Person";
      
  }
  
  /*********  Student.java   子类继承自Person  ***********/
  package com.kinvy.oop.demo02;
  
  //子类  继承自Person
  public class Student extends Person {  //继承自Person
      public String name = "Student";
  
      public void test(String name) {
          System.out.println(name);		//输出的是传进来的name值
          System.out.println(this.name);	//输出当前类的name = Student
          System.out.println(super.name);	//输出父类的name = Person
      }
  
  }
  
  
  ```

  子类实例化时会自动调用父类的构造器，隐藏式的调用`super()`；

* super()注意点：
  1. super调用父类的构造方法，必须在构造方法的第一个
  2. super必须只能出现在子类的方法或构造方法中
  3. super和this不能同时调用构造方法

* VS  `this`

  代表的对象不同：

  ​	this: 本身调用者这个对象

  ​	super：代表父类对象的引用

  前提：

  ​	this： 没有继承也可以使用

  ​	super： 只能在继承条件才可以使用

  构造方法：

  ​	this() ：本类的构造

  ​	super()： 父类的构造

* 方法的重写

  ```java
  /************  Application.java  **************/
  package com.kinvy.oop;
  
  
  import com.kinvy.oop.demo02.Son;
  import com.kinvy.oop.demo02.Base;
  
  public class Application {
      public static void main(String[] args) {
  
          Son son = new Son();
          Base base = new Son();
          //静态方法
          son.test01();      //调用子类
          base.test01();   //调用父类
  
          System.out.println("------------------");
  
          //非静态方法
          son.test02();      //调用子类
          base.test02();   //调用父类
  
      }
  }
  
  
  /*************   Base.java   父类   **************/
  package com.kinvy.oop.demo02;
  
  public class Base {
      public static void test01() {
  
          System.out.println("Base test01()");
      }
  
      public  void test02() {
  
          System.out.println("Base test02()");
      }
  }
  
  
  /*********  Son.java   子类继承自Person  ***********/
  package com.kinvy.oop.demo02;
  
  public class Son extends Base{
      public static void test01() {  //静态无法重写
          System.out.println("Son test01()");
      }
  
      @Override    //重写父类非静态方法
      public void test02() {
          System.out.println("Son test02()");
      }
  }
  
  
  ```

  重写：需要有继承关系，子类重写父类的方法

  1. 方法名必须相同
  2. 参数列表必须相同
  3. 修饰符：权限范围可以扩大 但不能缩小 `publi->protected->private`
  4. 抛出的异常：范围，可以被缩小，但不能扩大



* **多态：**

  ```java
  /************Application.java ******************/
  package com.kinvy.oop;
  
  
  import com.kinvy.oop.demo03.Person;
  import com.kinvy.oop.demo03.Student;
  
  public class Application {
      public static void main(String[] args) {
          //一个对象的实际类型是确定的
          new Student();
          new Person();
  
          //可以指向的引用类型就不确定了；父类的引用指向子类
  
          //Student 能调用的方法都是自己的或者继承父类的
          Student s1 = new Student();
          //Person 父类型， 可以指向子类，当时不能调用子类独有的方法
          Person s2 = new Student();
          Object s3 = new Student();
  
          s2.run();      //子类重写了父类的方法，执行子类的方法
          s1.run();
  
          ((Student) s2).eat();  //强制装换
      }
  }
  
  
  /************Person,java*************************/
  package com.kinvy.oop.demo03;
  
  public class Person {
      public void run() {
          System.out.println("person run");
      }
  }
  
  
  /************Student.java*********************/
  package com.kinvy.oop.demo03;
  
  public class Student extends Person {
      @Override
      public void run() {
          System.out.println("student run");
      }
  
      public void eat() {
          System.out.println("student eat");
      }
  }
  
  
  ```

  

  多态注意事项：

  1. 多态是方法的多态，属性没有多态

  2. 父类和子类，有联系，类型转换异常 ！  ClassCast

  3. 存在条件：继承关系，方法需要重写，父类引用指向子类对象！  father f1 = new son();

     ​	不可以重写的方法：	`static方法` `final常量` `private方法`

  

  * `instanceof` 关键字

  



### 5. 抽象类和接口



### 6.内部类及OOP实战




