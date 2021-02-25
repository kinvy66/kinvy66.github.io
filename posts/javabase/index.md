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






