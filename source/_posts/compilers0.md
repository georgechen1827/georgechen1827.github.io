---
title: 编译原理相关知识
categories: [notes,学位课程]
tags: [编译原理,learning]
date: 2020-02-24 16:32:03
---

未完结,持续更新

---

课程内容:
* 编译器构造的一般原理和基本实现方法
* 理论知识: 形式语言和自动机理论,语法制导的定义和属性方法,程序分析原理
* 强调形式描述技术和自动生成技术
* 强调对编译原理和技术的宏观理解,不把注意力分散到枝节算法,不偏向于任何源语言或目标机器

<!--more-->

## 绪论

### 编译原理概述

语言处理器: 由编译器,解释器,汇编器,连接器,加载器,调试器及程序概要提取工具等所构成的集成软件开发环境  

* 机器语言和汇编语言: 第一和第二代程序设计语言  
* 高级语言: 能够自动进行内存管理,类型一致性检查等功能的程序设计语言   

翻译器: 能完成一种语言到另一种语言变换的软件

翻译器的不同形式:
* 编译器(c,c++): 从源程序通过编译器得到目标程序,从输入通过目标程序得到输出(效率高,平台相关)
* 解释器(Python,JavaScript): 从源程序和输入经过解释器直接得到输出 (平台无关)  
*区别: 编译器通过翻译来生成目标程序,解释器直接生成源程序指定的运算*
* 混和编译器(Java,C#): 源程序通过翻译器得到中间程序,中间程序和输入经过虚拟机得到输出(效率稍高,平台无关,但每个平台都要装虚拟机)

语言处理系统: 预处理器,编译器,汇编器,连接器\加载器  
  
主要流程: 源程序->修改后的源程序->目标汇编程序->可重定位的机器代码-(库文件,可重定位目标文件)>可执行目标程序

### 编译器基本结构

编译器: 将源程序编译为目标可执行程序的系统  
特点: 目标语言比源语言低级

#### 编译器结构
* 分析部分,前端: 源程序->中间表示
* 综合部分,后端: 中间表示->目标程序

前端,只依赖于源语言: 词法分析->语法分析->语义分析->中间代码生成
* 词法分析: 识别词法单元,如变量、数字等
* 语法分析: 识别语句,得到语法树
* 语义分析: 识别语义的合理性,得到语义分析结果
* 中间代码生成: 得到中间表示

后端,独立于源语言;和中间语言与目标机器有关: ->代码优化->代码生成
* 代码优化: 得到中间表示
* 代码生成: 得到可执行程序

同一前端和不同后端组合可以得到同一源语言在不同机器上的编译器  
不同前端和同一后端组合可以得到同一机器上的几个编译器

总体过程可以如下表示:  
![progress](proc0.png)  
编译的几个阶段常用一趟/遍（pass）扫描来实现，一趟/遍扫描 包括读一个输入文件和写一个输出文件。
#### 词法分析
逐个扫描构成源程序的字符,把它们组成词法单元(token)流
``` c
position = rate * 60
```
词法单元:
* 标识符: position,rate
* 运算符: *
* 赋值符: =
* 数字: 60

词法分析结果: *<id,1> <=> <id,2> <\*> <60>*  

词法分析也可以叫做线性分析或扫描

#### 语法分析
把词法单元流依照语言的语法结构按层次分组,来形式化成语法短语
``` c
position = rate * 60
```
构建语法树:
![grammer analysis](ga0.png)

表达式、语句等程序层次结构通常由递归的规则表示

#### 语义分析
检查程序语义的正确性,保证程序各个部分能有意义地结合在一起,为后面代码生成阶段手机类型信息  

语义分析包括:
* 类型转换
* 类型检查
* 语法制导翻译

语义分析结果:  
![grammer analysis](ga1.png)

#### 中间代码生成
生成一个位于高级编程语言和机器语言(目标程序)之间的中间代码  

一般有后缀表示,抽象语法树,三地址码表示法:  
![grammer analysis](ga2.png)  
*三地址码表示中只有三个变量*

#### 代码优化
改进代码,以产生执行较快的机器代码:  
![grammer analysis](ga3.png)

#### 目标程序生成
生成可以重定位的机器代码或汇编码:  
![grammer analysis](ga4.png)  
* 为源程序所用的每个变量选择存储单元，并且把中间代码翻译成等价的机器指令序列。
* 关键问题是寄存器分配

#### 关于符号表管理
编译器的一项重要工作是记录源程序中使用的标识符，并收集每个标识符的各种属性  
* 这些属性提供标识符的存储分配、类型和作用域信息  
* 如果是过程标识符，还有参数的个数和类型、参数传递方式和返回值类型  

符号表是为每个标识符保存一个记录的数据结构，记录的域是标识符的属性   
* 该数据结构允许我们迅速地找到一个标识符的记录，在此记录中存储和读取数据 

管理符号表:
* 词法分析器发现源程序的标识符时，把该标识符填入符号表;但是,词法分析期间不能确定一个标识符的属性
* 其余的阶段把标识符的信息填入符号表，然后以不同的方式使用这些信息

![grammer analysis](ga5.png)

#### 关于出错管理
每个阶段都可能发现源程序的错误。发现错误后，该阶段必须处理此错误，使得编译可以继续进行，以便进一步发现源程序的其他错误。
* 词法分析：当前被扫描的字符串不能形成语言的词法记号。
* 语法分析：记号流违反语言的语法规则。
* 语义分析：编译器试图找出语法正确但对所含的操作来说是无意义的结构，如相加的两个标识符，其一是数组名，另一个是过程名。

## 一个简单的语法制导翻译器
语法制导翻译器:
* 词法分析
* 语法分析(上下文无关文法)
* 中间代码生成(语法知道翻译)

前端模型如下:  
![grammer analysis](ga5.png)

### 词法分析
源程序--(词法分析器)->词法单元序列

#### 词法分析基本原理
词法分析基本步骤:
* 剔除空白和注释
* 识别和计算常量
* 识别关键字和标识符  

创建一个符合语法的状态机,并优化,编程实现它

下面代码可以不用细看,后面会细讲  
#### 剔除空白和注释
```java
for ( ; ; peek = next input character) {    // peek为预读字符
       if( peek is a blank or a tab ) do nothing;
       else if( peek is a newline) 
              line = line + 1;
       else break;
}
```
剔除空行和空白,直到扫描到下一个有效词法单元

#### 识别和计算常量
```java
if ( peek holds a digit) {
       v = 0;
       do {
               v = v * 10 + integer value of digit peek;
               peek = next  input  character
        }while ( peek holds a digit);
        return token (num, v);
}
```

#### 识别关键字和标识符
```java
if ( peek 存放了一个字母) {
     将字母或数位读入一个缓冲区b;
      s = b 中的字符形成的字符串;
      w = words.get(s) 返回的词法单元；
      if ( w 不是 null) return w;
      else {
             将键-值对(s, <id, s>)加入到words;
              return 词法单元<id, s>;
      }
}
```

#### 主流程
```java
Token scan () {
       跳过空白符；
       处理数字；
       处理保留字和标识符；
       /*如果运行到这里，就将预读字符peek作为一个词法单元*/
       Token t = new Token (peek);
        peek = 空白符 /*按照预读的规则进行初始化,参见龙书p48*/；
        return t;
}
```

#### 词法分析建立的类
各个对象关系如下:  
![relatives](proc1.png)

### 语法分析
语法分析是决定如何使用一个文法生成一个终结符号串的过程

举例如下:  
![analysis](proc3.png)  

步骤:
* 根据语法构建文法
* 根据文法构建预测分析表(LL文法,LR文法)

#### 上下文无关文法 CFG
上下文无关文法(Context Free Grammar)由一个四元组G构成  
![grammer](gra0.png)

在这里，有  
![grammer](gra1.png)

例如，由+，-号分隔的数位序列可以由如下语法表示  
```java
// 终结符号集合 {0,1,2,3,4,5,6,7,8,9,+,-} (叶子节点)
// 非终结符号集合 {list,digit}
// 产生式集合:{
    list->list+digit
    list->list-digit
    list->digit
    digit->0|1|2|3|4|5|6|7|8|9
}
// 开始符号 list
```
#### 预测分析表
NaN

#### 语法分析树
语法分析树用图形的方式展现从文法的开始符号推出相应符号串的过程  

从定义上看,给定一个上下文无关文法,该文法的一棵语法分析树(parse tree)是具有如下性质的树:
1. 根节点的标号为文法的开始符号
2. 每个叶子节点的标号为一个终结符号或空串(e)
3. 每个内部节点的标号为一个非终结符号
4. 如果非终结符号A是某个内部节点的标号,并且它的子节点的标号从左到右分别为X1,X2...Xn,那么必然存在产生式A->X1,X2...Xn, 其中X1...Xn既可以是终结符号也可以是非终结符号

例如:  
![tree](tree0.png)

#### 左递归问题的消除
原始公式:
```java
A -> A x | y
```
这种公式在考虑FRONT(A)时会遇到无穷递归的问题


改进公式:将左递归化为循环
```java
A -> x R
R -> y R | e(空白符)
```

效果如下:  
![recursive](recu0.png)

### 语法制导翻译
语法制导翻译的两种方式:
* 语法制导定义
* 语法制导翻译方案

#### 语法制导定义
* 每一个产生式和一组语义规则相关联
* 每个文法符号(非终结符)和一个属性集合相关联

此时,产生式和语义规则是分离的,如下:  
![trans](trans0.png)
语法制导定义类似于一种属性文法

#### 语法制导翻译方案
* 将程序片段附加到一个文法的各个产生式上的表示
* 被嵌入到产生式体中的程序片段成为语义动作,语义动作用花括号括起来

此时,语义是嵌入到产生式中的,如下:  
![trans](trans1.png)

## 词法分析概述
![lex](lex0.png)

* 词法记号：由记号名和属性值构成的二元组，属性值不是必须项，记号名是语法分析的输入符号。(这个模式的名字)
* 模式：一个记号的模式描述属于该记号的词法单元的形式。和一个给定模式匹配的字（字符串）的集合成为该模式的语言。(一个词法单元可能具有的形式)
* 词法单元：是源程序中匹配一个记号模式的字符序列，由词法分析器识别为该记号的一个实例。(一个具体的词法单元)

常见的词法分析生成器:lex,flex,jlex,ply等  

### 串和语言的定义
* 字母表：符号的有限集合
* 串：符号的有穷序列,空串为$\epsilon$
* 语言：字母表上的一个串集,可以只包含空串或是空集
* 句子：属于语言的串

串的运算:  
![lex](lex1.png)

### 正则表达式

#### 正则表达式的递归定义   
![re](re0.png)

#### 正则表达式的一些公理
![re](re1.png)

#### 正则定义
![re](re2.png)

#### 正则表达式的扩展
为了方便书写,对一些常用的正则表达式做如下定义  
![re](re3.png)  
![re](re4.png)  

一些数量方面的运算符也做了扩展  
![re](re5.png)  
![re](re6.png)

#### 状态转换图
状态转换图描述词法分析器被语法分析器调用时，词法分析器为返回下一个记号所做的动作

绘制状态转换图是构造词法分析器的第一步
* 圆圈表示状态，开始状态由一条没有出发节点、标号为“开始”的边指明
* 双层圆圈表示接受状态，表示已识别一个记号
* 有向边表示从一个状态到另一状态
* 每条边的标号包含一个或多个符号，若离开状态s的某边上标号为other，则它表示离开s的其他边所指示的字符以外的任意字符
* \*表示输入指针必须回退的转态

![status](status0.png)

### 有限状态自动机

#### 不确定的有限状态自动机NFA
* $Q$是非空有穷的状态集合
* $\Sigma$是非空有穷的输入字母表
* $\delta$为一个$Q \times (\Sigma \cup \lbrace \epsilon \rbrace) \to \rho(Q)$上的映射,$\rho(Q)$表示Q的幂集
* $q_0 \in Q$是初始状态
* $F \subseteq Q$是接受状态集合  
> 此时,这个自动机在确定的状态接收到了一个确定的符号后,其下一个状态时不确定的

#### 确定的有限状态自动机DFA
* $Q$是非空有穷的状态集合
* $\Sigma$是非空有穷的输入字母表
* $\delta$为一个$Q \times \Sigma \to Q$上的映射,是状态转移函数
* $q_0 \in Q$是初始状态
* $F \subseteq Q$是接受状态集合
>* 一个符号标记离开同一状态只有一条边
>* 任何状态下都没有ε转换

### 基于MYT算法从正则表达式到NFA
正则表达式-(MYT算法)>NFA-(子集构造算法)>DFA-(hopcorft最小化算法)>词法分析器代码

#### MYT算法
基本思路: 对正则表达式的结构做归纳  

* 一些基本元素如下构造  
![cons](construct0.png)  
![cons](construct1.png)  
![cons](construct2.png)  
![cons](construct3.png)  

正则表达式的分解和构造:  
![cons](construct4.png)

#### 从NFA到DFA的转换(子集构造算法)
* 找出字母表
* 分析转换过程(注意$\epsilon$状态可以进行多次输入/滑行),得到DFA
>1. 以初始状态为中心,将它接受$\epsilon$所能滑行到的状态和这个状态设为一个新状态
>2. 扫描字母表,将新状态接受相同字母所能到达的所有状态设合并为一个状态
>3. 以2.中所得到的状态为中心执行操作1.,直到没有新状态产生  

一些概念:
![cons](construct5.png)  

子集构造算法不一定得到最简的DFA

#### DFA的化简
目标: 使得DFA的状态最少
* 找出字母表
* 分析DFA转换过程,得到最简DFA
* 主要思想:对状态进行最小划分
* 化简条件:化简前DFA的函数应是全函数(对每一个状态s和输入a都有对应输出状态)
>0. 如果DFA不是全函数,需要引入非终结的死状态E
>>* 所有未定义的输出状态全部转到死状态E
>>* 死状态接受E的所有输入都转换到本身
>1. 构造状态集合的初始划分$\Pi$={接收状态,非接收状态}
>2. 对$\Pi$中每个子集G,对G进行如下划分:
>> 把G划分为若干子集，G的两个状态s和t在同一子集中，当且仅当对任意输入符号a，s和t的a转换都到π的同一子集中
>3. 重复2.直到$\Pi$不再改变
>4. 去除死状态,得到最简的状态集合:
>>* 删除死状态和所有和这个状态连接的边,所有边都改成无定义
>>* 从开始状态不可达到的状态也删除

### 直接从正则表达式到DFA
NaN

## 语法分析概述
语法分析器读取词法分析器提供的记号流，检查它是否能由源语言的文法产生，输出分析树的某种表示。

![token](token0.png)

语法分析器类型:
* 通用语法分析（Cocke-Younger-Kasami算法，Earley算法）:效率低
* 自顶向下语法分析: 从语法分析树的根节点开始向叶子节点构造语法分析树
* 自底向上语法分析: 从叶子结点开始，逐渐向根节点方向构造语法分析树


---

*待更新...*

















