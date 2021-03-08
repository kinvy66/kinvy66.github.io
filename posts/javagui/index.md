# Java GUI 编程


<!--more-->



# GUI编程



## 1. 简介

Gui核心技术： Swing   AWT

1. 界面不美观
2. 需要jre环境



## 2. AWT

### 2.1 Awt介绍

1. 包含了很多类和接口！ GUI！
2. 元素： 窗口，按钮，文本框
3. java.awtz



### 2.2 组件容器介绍

#### 2.2.1 frame

```java
package com.kinvy.lesson01;

import java.awt.*;

public class TestFrame {
    public static void main(String[] args) {
        //Fram
        Frame frame = new Frame("Tile 标题");

        //需要设置可见型
        frame.setVisible(true);
        //设置窗口大小
        frame.setSize(400,400);
        //设置窗口背景颜色
        frame.setBackground(Color.BLACK);
        //弹出的初始位置
        frame.setLocation(200,200);
        //设置大小固定
        frame.setResizable(false);
    }
}

```



封装自己的Frame类，展示多个窗口

```java
package com.kinvy.lesson01;

import java.awt.*;

public class TestFrame02 {
    public static void main(String[] args) {
        //展示多个窗口
        new MyFrame(100,100,200,200,Color.BLUE);
        new MyFrame(300,100,200,200,Color.YELLOW);
        new MyFrame(100,300,200,200,Color.RED);
        new MyFrame(300,300,200,200,Color.MAGENTA);

    }
}

//继承Frame
class MyFrame extends Frame{
    static int id = 0;  //窗口计数器

    public MyFrame(int x, int y, int w, int h,Color c) {
        super("MyFrame+"+(++id));
        setBackground(c);
        setBounds(x,y,w,h);
        setVisible(true);
    }
}
```

![image-20210228164311164](https://kinvy-images.oss-cn-beijing.aliyuncs.com/Images/image-20210228164311164.png)



#### 2.2.2 panel面板

```java
package com.kinvy.lesson01;

import java.awt.*;
import java.awt.event.WindowAdapter;
import java.awt.event.WindowEvent;

public class TestPanel {
    public static void main(String[] args) {
        Frame frame = new Frame();

        //布局的概念
        Panel panel = new Panel();

        //设置布局
        frame.setLayout(null);

        //坐标
        frame.setBounds(300,300,500,500);
        frame.setBackground(new Color(0xDC1C1C));

        //panel设置坐标 相对于frame
        panel.setBounds(50,50,400,400);
        panel.setBackground(new Color(0x62BAEA));

        frame.add(panel);
        frame.setVisible(true);

        //监听事件，监听窗口关闭事件
        frame.addWindowListener(new WindowAdapter() {
            //窗口关闭时的动作
            @Override
            public void windowClosing(WindowEvent e) {
                //结束程序
                System.exit(0);
            }
        });

    }
}

```







### 3. Swing


