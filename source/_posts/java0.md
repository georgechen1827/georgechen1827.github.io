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

<!--more-->

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
NaN

#### eclips

java里的程序应当都以工程的形式存在

* 新建一个工程，起一个名字(文件夹的名字)
* 在src文件夹中建立package包(一般小写字母)
* 在package里面建立类(首字母大写)
* 写主函数...
* 右击包文件 run as application

## Java数据运算,流程控制和数组

数据类型决定数据的存储方式和运算方式

主要有两类数据类型:
* 基本数据类型(实体直接存储在栈里)
* 引用数据类型(实体存储在堆里)
> 赋值时,基本类型复制的是值,引用类型复制的是引用

### 基本数据类型
* 整数型(byte,short,int,long(3.14L))
* 浮点数型
* 逻辑型
* 字符型

### 运算符与表达式
* 短路与:&& 短路或||
* 注意: ^不是乘方,是位运算异或
* 赋值的强制类型转换
* 字符串连接运算符:+ 可以将非字符串类型转换成字符串类型并连接

### 流程控制语句
*类似C++*
### 数组
*类似C++*

## Java的类

### 字段和方法
* 字段是类的属性
* 方法时类内部的函数

Java的对象时通过引用来表示的，没有指针

### 方法重载
方法重载是指多个方法有相同的名字，但编译的时候能识别出来
* 同通过方法重载可以实现多态

### this指针
类中this可以解决局部变量与域同名的问题，也可以用来调用另一个构造方法:```this(args**)```

### 继承
java一个类只能有一个直接父类
* 子类继承父类的状态和行为
* 子类可以修改父类的状态或重载父类的行为
* 子类可以添加新的状态和行为
```java
class c1 extends c2{
    ...
}
```
在UML图中,继承用箭头表示

### 方法覆盖
方法覆盖可以用```@override```标注

### super的使用
* 使用super在同名的情况下可以在类内访问父类的方法
* super可以在子类的构造函数中调用父类的构造函数```super(args**)```

### 父类对象和子类对象转换
子类对象可以赋值给父类对象,反之不行

### 包
包和子包的定义,实际上时为了解决名字空间,名字冲突的问题
* 同一个包中的类,默认情况下可以互相访问

#### package语句和import导入语句
package可以封装包,import可以导入包

### 访问控制符
访问修饰符和C++类似C
* 默认情况是一种包内可访问性

非访问控制符:
* static静态类,静态成员
* final最终的类,成员,方法
* abstract抽象类,抽象成员

### 接口
定义接口```interface i1```
* 接口所有方法都自动是public abstract  
实现接口implements
* 实现接口可以解决多继承问题
* 实现接口与类的继承无关

## Java内的一些机制

### 变量及其传递
变量分为基本类型和引用类型

变量也可以分为字段变量和局部变量
* 字段变量在堆中存储，局部变量在栈中存储
* 字段变量可以自动赋初始值，局部变量要显式赋值
* 相对于字段变量，局部变量不能被访问控制符或static修饰，但可以被final修饰
* Java参数传递是值传递(引用变量传递的是引用值)

### 多态和虚方法调用
* 编译时的多态: 重载
* 运行时的多态: 覆盖,动态绑定(虚方法调用)
>* 所有的非final方法都会进行动态绑定

上溯造型: 将派生类当作基本类处理

### 虚方法
* Java中,普通的方法是虚方法
* static,private方法不是虚方法调用(编译后的指令是不同的)

### 构造方法
对象都有构造方法,包括抽象类

* 实例初始化: 在类中直接写{}
* 静态初始化: 在类中写static {}

### 构造方法执行过程
* 调用本类或父类构造方法直到objct类
* 按照声明顺序执行字段的初始化赋值
* 执行构造方法中的语句

### 对象清除与对象回收
Java中对象销毁是自动的,不需要进行delete

System.gc()可以建议系统进行垃圾回收

Java中没有析构方法,但子类可以重写finalize()方法

### 内部类和匿名类

#### 内部类
在类内定义class即为内部类

### java异常处理
Java中用try-catch捕获并处理异常，用throw来抛出异常

---
*待更新...*













