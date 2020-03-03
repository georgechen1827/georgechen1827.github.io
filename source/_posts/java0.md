---
title: Java学习笔记
categories: [notes,学位课程]
tags: [java,learning]
date: 2020-02-24 08:33:24
---

未完结,持续更新

---

## Java常识

Java: 一次编译，处处运行

### Java特点

c++ - -

* 无直接指针操作
* 自动内存管理
* 数据类型长度固定
* 不用头文件
* 不包含结构和联合
* 不支持宏
* 不用多重继承(接口实现)
* 无类外全局变量
* 无goto

Java三种核心机制

* Java虚拟机
* 代码安全性监测
* 垃圾回收机制

*Java程序都是运行在虚拟机之上的,与平台无关*

* JRE(java运行环境)=JVM+API
* JDK(Java开发工具包)=JRE+Tools

### Java面向对象程序设计

类

* 属性: 变量,字段
* 行为: 函数,方法

类与对象的关系

* 类是对象的抽象
* 对象是类的实例

面向对象三大特性

* 封装: 模块化,信息隐蔽
* 继承: 父类子类间共享数据,更好地抽象和分类,增强代码重用性和可维护性
* 多态: 方法重载

### 简单Java程序

Java程序类型:

* Application: 独立程序,需要执行器(虚拟机)来运行
* Applect: 非独立程序,嵌入在HTML网页中运行

应用程序要点(helloword)

* class是主体
* public类名与文件名同名
* main()的写法是固定的: public static void main()
* System.out.print及println及printf

Applet程序(helloword)

* import表示导入
* extends JApplet表示继承
* 有paint()方法,表示如何绘制
* 没有main()方法

Java程序基本构成

* package语句(0或1句)
* import语句(0或多句)
* 类定义(1或多个,但只能有一个public类,与文件同名)

### Java程序开发过程

编辑,编译与运行

* 编辑: 编辑器编辑,文件名要与public class类名一致
* 程序编译: 转换程序为字节码,扩展名.class  javac name.java
* 程序运行: 执行.class中的文件    java name

JDK安装目录

> Bin 存放工具文件
> Jre 存放与Java运行环境相关的文件
> Demo 存放示例文件
> Include 存放与C相关的头文件
> Lib 存放程序库
> DB 数据库相关

### Java的几个工具

主要工具

* javac 编译
* java 运行(控制台及图形界面程序)
* javaw 运行图形界面程序
* appletViewer 运行applet程序

另外常用工具

* jar 打包工具
* javadoc 生成文档
* javap 查看类信息及反汇编

### Java的输入和输出

#### 文本界面: 使用Scanner类
使用java.util.Scanner类
* Scanner.nextInt()
* Scanner.nextDouble()
* Scanner.next 得到下一个单词
```java
import java.util.Scanner
class ScannerTest{
    public static void main( String[] args){
        Scanner scanner = new Scanner(System.in);
        int a = scanner.nextInt();
    }
}
```

#### 使用in及out
使用java.io包
* System.in.read()
* System.out.print()
```java
char c = '';
System.out.print('Hello');
try{
    c = (char)System.in.read();
}catch(IOExceprion e){}
```

#### 图形界面输入输出
添加按钮,监听事件...

### 集成开发环境

#### eclips

java里的程序应当都以工程的形式存在

* 新建一个工程，起一个名字(文件夹的名字)
* 在src文件夹中建立package包(一般小写字母)
* 在package里面建立类(首字母大写)
* 写主函数...
* 右击包文件 run as application

---
*待更新...*













