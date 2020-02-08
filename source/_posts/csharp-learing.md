---
title: 'c# notes'
categories: notes
tags: [c#,learning]
date: 2020-02-06 16:48:15
---

源:<https://www.runoob.com/csharp/csharp-tutorial.html>

## c#入门

### 特点

特性:

> 现代的、通用的编程语言  
> 面向对象  
> 面向组件  
> 容易学习  
> 结构化语言  
> 它产生高效率的程序  
> 它可以在多种计算机平台上编译  
> .Net 框架的一部分  

重要功能:

> 布尔条件（Boolean Conditions）  
> 自动垃圾回收（Automatic Garbage Collection）  
> 标准库（Standard Library）  
> 组件版本（Assembly Versioning）  
> 属性（Properties）和事件（Events）  
> 委托（Delegates）和事件管理（Events Management）  
> 易于使用的泛型（Generics）  
> 索引器（Indexers）  
> 条件编译（Conditional Compilation）  
> 简单的多线程（Multithreading）  
> LINQ 和 Lambda 表达式  
> 集成 Windows  

.net框架:  
.Net 框架是一个创新的平台，能帮您编写出下面类型的应用程序：

> Windows 应用程序  
> Web 应用程序  
> Web 服务  

.Net 框架应用程序是多平台的应用程序。框架的设计方式使它适用于下列各种语言：C#、C++、Visual Basic、Jscript、COBOL 等等。所有这些语言可以访问框架，彼此之间也可以互相交互。

> .Net 框架由一个巨大的代码库组成，用于 C# 等客户端语言。下面列出一些 .Net 框架的组件：  
> 公共语言运行库（Common Language Runtime - CLR）  
> .Net 框架类库（.Net Framework Class Library）  
> 公共语言规范（Common Language Specification）  
> 通用类型系统（Common Type System）  
> 元数据（Metadata）和组件（Assemblies）  
> Windows 窗体（Windows Forms）  
> ASP.Net 和 ASP.Net AJAX  
> ADO.Net  
> Windows 工作流基础（Windows Workflow Foundation - WF）  
> Windows 显示基础（Windows Presentation Foundation）  
> Windows 通信基础（Windows Communication Foundation - WCF）  
> LINQ    

### 程序结构

```c#
using System;   //使用名字空间
namespace HelloWorldApplication //一个名字空间
{
   class HelloWorld //一个类
   {    //类方法、类属性
      static void Main(string[] args)   //main方法
      {
         /* 我的第一个 C# 程序*/
         Console.WriteLine("Hello World");
         Console.ReadKey();
      }
   }
}
```

说明:

* 程序的第一行 using System; - using 关键字用于在程序中包含 System 命名空间。 一个程序一般有多个 using 语句。
* 下一行是 namespace 声明。一个 namespace 里包含了一系列的类。HelloWorldApplication 命名空间包含了类 HelloWorld。
* 下一行是 class 声明。类 HelloWorld 包含了程序使用的数据和方法声明。类一般包含多个方法。方法定义了类的行为。在这里，HelloWorld 类只有一个 Main 方法。
* 下一行定义了 Main 方法，是所有 C# 程序的 入口点。Main 方法说明当执行时 类将做什么动作。
* 下一行 /*...*/ 将会被编译器忽略，且它会在程序中添加额外的 注释。
* Main 方法通过语句 Console.WriteLine("Hello World"); 指定了它的行为。 
* WriteLine 是一个定义在 System 命名空间中的 Console 类的一个方法。该语句会在屏幕上显示消息 "Hello, World!"。
* 最后一行 Console.ReadKey(); 是针对 VS.NET 用户的。这使得程序会等待一个按键的动作，防止程序从 Visual Studio .NET 启动时屏幕会快速运行并关闭。  

以下几点值得注意：

* C# 是大小写敏感的。
* 所有的语句和表达式必须以分号（;）结尾。
* 程序的执行从 Main 方法开始。
* 与 Java 不同的是，文件名可以不同于类的名称

### 一些基础知识

#### 可空类型

\<data_type\>?或Nullable\<data_type\>表示一个可空类型,其除了可以被data_type范围内的对象赋值之外还可以被赋值为null  

```c#
int? i = 3 
等同于
Nullable<int> i = new Nullable<int>(3);

int i; //默认值0
int? i; //默认值null
```

'??'运算:Null合并运算符  

```c#
using System;
namespace CalculatorApplication
{
   class NullablesAtShow
   {
         
      static void Main(string[] args)
      {
         
         double? num1 = null;
         double? num2 = 3.14157;
         double num3;
         num3 = num1 ?? 5.34;      // num1 如果为空值则返回 5.34
         Console.WriteLine("num3 的值： {0}", num3);
         num3 = num2 ?? 5.34;
         Console.WriteLine("num3 的值： {0}", num3);
         Console.ReadLine();

      }
   }
}
```

#### 其他

数据类型<https://www.runoob.com/csharp/csharp-data-types.html>  
类型转换<https://www.runoob.com/csharp/csharp-type-conversion.html>  
变量<https://www.runoob.com/csharp/csharp-variables.html>  
常量<https://www.runoob.com/csharp/csharp-constants.html>  
运算符<https://www.runoob.com/csharp/csharp-operators.html>  
数组<https://www.runoob.com/csharp/csharp-array.html>  
字符串<https://www.runoob.com/csharp/csharp-string.html>  
枚举<https://www.runoob.com/csharp/csharp-enum.html>   

名字空间<https://www.runoob.com/csharp/csharp-namespace.html>  
预处理命令<https://www.runoob.com/csharp/csharp-preprocessor-directives.html>  
正则表达式<https://www.runoob.com/csharp/csharp-regular-expressions.html>  
异常处理<https://www.runoob.com/csharp/csharp-exception-handling.html>  
文件操作<https://www.runoob.com/csharp/csharp-file-io.html>  

### 判断循环

判断:  

```c#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace jiecheng
{
    class jiecheng
    {
        public int Jc(int num)
        {
            
            return num > 0 ? num *Jc(num - 1):1;  //如果num>0则返回num *Jc(num - 1)，否则返回1
        }
    }

    class excutejiecheng
  
    {
        static void Main(string[] args)
        {
            jiecheng n = new jiecheng();
            int result = n.Jc(Convert.ToInt16(Console.ReadLine()));
            Console.WriteLine("result is {0}",result);
            Console.ReadKey();
        }
    }
}
```

循环:  

```c#
using System;

namespace Loops
{
    
    class Program
    {
        static void Main(string[] args)
        {
            for (; ; )
            {
                Console.WriteLine("Hey! I am Trapped");
            }
 
        }
    }
}
```

### 面向对象

```c#
using System;

namespace RectangleApplication
{
    class Rectangle
    {
        //成员变量
        public double length;
        public double width;

        public double GetArea()
        {
            return length * width;
        }
        public void Display()
        {
            Console.WriteLine("长度： {0}", length);
            Console.WriteLine("宽度： {0}", width);
            Console.WriteLine("面积： {0}", GetArea());
        }
    }// Rectangle 结束

    class ExecuteRectangle
    {
        static void Main(string[] args)
        {
            Rectangle r = new Rectangle();
            r.length = 4.5;
            r.width = 3.5;
            r.Display();
            Console.ReadLine();
        }
    }
}
```

封装<https://www.runoob.com/csharp/csharp-encapsulation.html>  
方法<https://www.runoob.com/csharp/csharp-methods.html>  
结构体<https://www.runoob.com/csharp/csharp-struct.html>  
类<https://www.runoob.com/csharp/csharp-class.html>  
继承<https://www.runoob.com/csharp/csharp-inheritance.html>  
多态<https://www.runoob.com/csharp/csharp-polymorphism.html>  
重载运算符<https://www.runoob.com/csharp/csharp-operator-overloading.html>  
接口<https://www.runoob.com/csharp/csharp-interface.html>






























