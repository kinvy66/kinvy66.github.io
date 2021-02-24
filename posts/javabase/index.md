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






