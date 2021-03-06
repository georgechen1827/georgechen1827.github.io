---
title: 形式语言和自动机初步
categories: notes
tags: [编译原理,learning]
date: 2020-03-04 16:23:51
---

参考离散数学(清华大学出版社,第五版)相关内容  

ps: 编辑公式真费时间$\to$_$\to$

---

自动机是描述计算的数学模型,用来识别语言或计算函数. 形式文法也是一种数学模型,用来产生形式语言. 形式语言和自动机理论密切相关,是计算机科学和技术的重要理论基础.  

本文扼要地介绍形式文法的基本概念,有穷自动机和图灵机以及它们识别的语言类,其他不做分析

<!--more-->

## 形式语言和形式文法

形式语言的描述最早在1956年由语言学家乔姆斯基建立

在乔姆斯基的分类中,形式文法一共有如下几类:
* 0型文法: 现证明等价于图灵机(下同)
* 1型文法: 等价于非确定型线性界限自动机
* 2型文法: 等价于非确定型下推自动机
* 3型文法: 等价于有穷自动机

形式文法,特别是上下文无关文法(2型文法)和正则文法(3型文法)在程序设计语言和编译理论中起着重要的作用

### 字符串和形式语言

抽象而言,语言是按照一定规则排列的符号的集合

定义:

* 字母表$\Sigma$: 一个非空的有穷集合
* 字符串$\omega$: 由$\Sigma$中的符号组成的有穷序列,如$a_ia_j...a_k$; 特别地,$aaa...a$记作$a^n$
* $\vert \omega \vert$: 字符串$\omega$的长度, 空串$\epsilon$长度为0  


* 形式语言(语言): $\Sigma^\*$的任何子集称作字母表$\Sigma$上的形式语言, 其中,$\Sigma^\*$是$\Sigma$上字符串的全体  

> $\emptyset, \lbrace \epsilon \rbrace, \Sigma^\*$都是$\Sigma$上的语言. 注意,前两者是不同的

在字符串$\omega$中:
* 前缀: 由$\omega$左端若干个连续符号组成的字符串
* 后缀: 由$\omega$右端若干个连续符号组成的字符串
* 字串: 由$\omega$任何部位若干个连续符号组成的字符串
* 连接运算: $\omega_1\omega_2$表示把$\omega_2$接在$\omega_1$的右边, 显然,它是可结合的

### 形式文法

语言是由一定规则产生出来的,这种规则就是文法

例如,`9+5-2`这个字符串可由如下文法规则产生:

>1. 表达式->表达式+数字;  
>2. 表达式->表达式-数字;  
>3. 表达式->数字;
>4. 数字->2;  
>5. 数字->5;  
>6. 数字->9;

定义:
* 产生式: 文法中的每一条规则都叫做产生式
* 终结符: 不能产生其他字符串的符号, 如上述文法中的2,5,9
* 非终结符: 文法规则中除了终结符之外的其他符号,如`表达式`,`数字`,`+`,`-`

`9+5-2`的推理过程:
* 从`表达式`开始由2,1,3得到`数字+数字+数字`
* 由4,5,6可以得到`9+5-2`

当然,这组规则不仅仅只能推出`9+5-2`  

注意: 规则所推出的字符串在语义上不一定正确,但在形式上都是合法的

#### 形式文法的定义
一个形式文法是一个有序四元组$G=<V,T,S,P>$, 其中:
* $V$是一个非空有限集合,集合的元素称作变元或**非终结符**
* $T$是一个非空有限集合,$V\cap T=\emptyset$,集合中的元素称作**终结符**
* $S\in V$称作**起始符**
* $P$是一个非空有穷集合,它的元素称作**产生式**或改写规则
&emsp; $P$中元素应有这样的形式: a->b; 其中a,b$\in (V\cup T)^\*$, 且a$\ne \epsilon$

#### 派生,生成语言

直接派生:
* 给定文法$G=<V,T,S,P>$,设$x,y \in (V \cup T)^\*$. 称**$y$是$x$的直接派生($x\Rightarrow y$)**,当且仅当:  
> $\exists u,v \in (V \cup T)^\* $ 且 $ \exists$ 'a->b' $\in P$ 使得 $x = uav,y = ubv$ (即把x中的a改写成b后得到y)  

派生:
* 给定文法$G=<V,T,S,P>$,设$x_1,x_2,...,x_n \in (V \cup T)^\*, n \ge 1 且 x_1\Rightarrow x_2 \Rightarrow ... \Rightarrow x_n $, 则称**$x_n$是由$x_1$派生出来的($x_1 \dot \Rightarrow x_n$)**  
> 注意,对$V \cup T$上的所有字符串$\omega$有$\omega \dot \Rightarrow \omega$. 可见$\dot \Rightarrow$是$\Rightarrow$的自反传递闭包  

生成语言:  
* 设$G=<V,T,S,P>$是一个文法,$L(G)$是文法G**生成的语言**,则$L(G)$满足
$$ L(G) = \lbrace \omega \in T^\* | S \dot \Rightarrow \omega \rbrace $$   
> 根据定义,$L(G)$中的字符串满足如下两个条件:
> 1. 字符串由终结符构成
> 2. 字符串可以由起始符派生出来

文法的等价
* 如果$L(G_1) = L(G_2)$,则称文法$G_1$和$G_2$**等价**

### 形式文法分类

#### 0型文法: 无限制文法
0型文法就是一般形式的文法,在形式文法定义的基础上不附加任何条件  

一个0型文法是一个有序四元组$G=<V,T,S,P>$, 其中:
* $V$是非终结符集合,非空有限
* $T$是终结符集合,非空有限,$V\cap T=\emptyset$
* $S\in V$是**起始符**
* $P$是产生式集合,非空有限

0型文法又称作短语结构文法或无限制文法,0型文法生成的语言称作0型语言

#### 1型文法: 上下文有关文法
1型文法在0型文法上加了一条限制: 对P中每一个产生式a->b都有$\vert a \vert \ge \vert b \vert$  

一个1型文法是一个有序四元组$G=<V,T,S,P>$, 其中:
* $V$是非终结符集合,非空有限
* $T$是终结符集合,非空有限,$V\cap T=\emptyset$
* $S\in V$是**起始符**
* $P$是产生式集合,非空有限
> $P$中元素应有这样的形式: 对P中任意一个产生式a->b都有$\vert a \vert \ge \vert b \vert$  

每一个1型文法都等价于这样一个文法(证明略),它的产生式形如  
$$ uAv \to u \alpha v $$  
> 这里$ A \in V, u,v \in (V \cup T)^\* ,\alpha \ne \epsilon$  

也就是说,在这种文法中,替换变元时必须考虑它的上下文,才能把$A$换成$\alpha$  

因此,1型文法又叫做上下文有关文法,若$L-\lbrace \epsilon \rbrace$可由1型文法生成,则L称作1型语言或上下文有关语言(1型文法本身不能生成$\epsilon$)

#### 2型文法: 上下文无关文法
2型文法在1型文法的基础上又做了一些限制(令上文中的$u,v = \epsilon$)

一个2型文法是一个有序四元组$G=<V,T,S,P>$, 其中:
* $V$是非终结符集合,非空有限
* $T$是终结符集合,非空有限,$V\cap T=\emptyset$
* $S\in V$是**起始符**
* $P$是产生式集合,非空有限
> $P$中元素应有这样的形式: $ A \to \alpha $; 其中$A \in V, \alpha \in (V\cup T)^\*$ _(0型文法是$A \in (V\cup T)^\*$)_  

此时,在这种文法中,替换变元时不需要考虑它的上下文

因此,2型文法又称作上下文无关文法,2型文法生成的语言称作2型语言或上下文无关语言

#### 3型文法: 正则文法
3型文法在2型文法的基础上做了更多的限制,其分为右线性文法和左线性文法

一个**右线性文法**是一个有序四元组$G=<V,T,S,P>$, 其中:
* $V$是非终结符集合,非空有限
* $T$是终结符集合,非空有限,$V\cap T=\emptyset$
* $S\in V$是**起始符**
* $P$是产生式集合,非空有限
> $P$中元素应有这样的形式: $ A \to \alpha B $或$ A \to \alpha $; 其中$A,B \in V, \alpha \in T^\*$ _(注意符号所属范围)_

一个**左线性文法**是一个有序四元组$G=<V,T,S,P>$, 其中:
* $V$是非终结符集合,非空有限
* $T$是终结符集合,非空有限,$V\cap T=\emptyset$
* $S\in V$是**起始符**
* $P$是产生式集合,非空有限
> $P$中元素应有这样的形式: $ A \to B \alpha $或$ A \to \alpha $; 其中$A,B \in V, \alpha \in T^\*$  

右线性文法和左线性文法统称做3型文法或正则文法,3型文法生成的语言称作3型语言或正则语言  

可以证明的是,每一个右线性文法都存在与之等价的左线性文法,反之亦然; 即每一个正则语言都可以同时用右线性文法和左线性文法生成

#### 几种形式文法生成的语言类之间的关系
这几种语言类之间存在着真包含关系
* 正则语言是上下文无关语言
* 上下文无关语言是上下文有关语言
* 上下文有关语言是0型语言

在编译原理中,词法分析可以用正则文法解决,而语法分析使用上下文无关文法

注: 在正则文法和上下文无关文法中,当同一个符号作为多个产生式的左端时,可以用"或"`|`来合在一起写

## 图灵机TM
图灵机是图灵于1936年提出的一种数学模型, 这个模型很好地描述了计算的过程. 大量事实表明, 任何算法都可以用一个图灵机来描述, 这就是Chruch论题.  

图灵机在可计算性理论中起着重要的作用, 可以证明, 图灵机识别的语言是0型语言

### 图灵机的基本模型
设想图灵机由一个控制器和一条无穷长的纸带组成,纸带分成了一个一个的小方格，每个方格有不同的颜色。有一个机器头在纸带上移来移去。机器头有一组内部状态，还有一些固定的程序。在每个时刻，机器头都要从当前纸带上读入一个方格信息，然后结合自己的内部状态查找程序表，根据程序输出信息到纸带方格上，并转换自己的内部状态，然后进行移动, 如下图:  
![TM](TM0.jpg)

#### 定义
图灵机是一个有序组$M = <Q, \Sigma, \Gamma, \delta, q_0, B, A>$, 其中
* $Q$是非空有穷的状态集合
* $\Sigma$是非空有穷的输入字母表
* $\Gamma$是非空有穷的带字母表且$\Sigma \subset \Gamma$
* $\delta$为一个$Q \times \Gamma \to \Gamma \times \lbrace L, R \rbrace \times Q$的映射,是动作函数
* $q_0 \in Q$是初始状态
* $B \in \Gamma - \Sigma$是空白符
* $A \subset Q$是接收状态的集合
> 对于$\delta$, 给定当前状态$q$和当前位置的符号$s$,它能将当前位置的符号改为$s'$、并且给出扫描头移动方向和次态$q'$; 即$\delta (q,s) = (s', L/R, q')$

显然,对于每一步计算,带上只有穷个方格的内容是非空白符,因此,纸带可以表示为$$Ba_1a_2...a_nB$$即两边都有无穷多个空白符的形式  

给定了图灵机M和纸带,为了描述计算中的每一步,这里又有一些定义:
* 格局: 计算中某一步时带上的内容、控制器的状态和读写头扫视的带方格称为M的一个格局
> 一般地,一个格局总可以表示成$\alpha_1 q \alpha_2$, 其中$\alpha_1, \alpha_2 \in \Gamma, q \in Q$  
> 这表示带上的内容为$\alpha_1 \alpha_2$, 当前状态为$q$, 读写头正在扫视$\alpha_2$的第一个字符(若$\alpha_2$是空串则扫视紧挨在右边的空白符)   
>* $q_0\omega$是M的初始格局,$\omega \in \Sigma^\*$是输入字符串  
* 接受格局: $\sigma = \alpha_1 q \alpha_2$中的$q$是接收状态,即$q \in A$
* 停机格局: $\sigma$时对应的&\delta (q,s)&没有定义,即图灵机不知道接下来一步要干什么  

* $\vdash$: 设$\sigma_1, \sigma_2$是两个格局, 如果从$\sigma_1$经过一步到达$sigma_2$,则记作$\sigma_1\vdash\sigma_2$
* $\dot \vdash$: 设$\sigma_1, \sigma_2$是两个格局, 如果从$\sigma_1$经过有限步到达$sigma_2$,则记作$\sigma_1\dot\vdash\sigma_2$  
* 计算: 一个格局序列$\sigma_1,\sigma_2,...,\sigma_n,...$(可以有穷也可以无穷)中每一个$\sigma_{i+1}$都能由$\sigma_i$一步得到,则称这个序列是一个计算

### 图灵机接受的语言
任给一个字符串$\omega$,从初始格局开始,图灵机M在字符串上的计算有如下三种可能:
* 停机在接受状态,此时称图灵机M接受字符串$\omega$
* 婷机在非接受状态,此时图灵机M不接受或拒绝字符串$\omega$
* 用不停机,此时也称图灵机M不接受或拒绝字符串$\omega$

则图灵机M接受的语言L(M)可定义为:
$$L(M) = \lbrace \omega | \omega \in \Sigma^\* , M接受\omega \rbrace$$

### 状态转移图
状态转移图是一个有向图,每一个节点代表一个状态; 初始状态用一个指向该节点的箭头标明, 终结状态用双圈标明; 边上应注明状态转换时的输入/输出

例如: 
![TM](TM1.png)

* 状态转移图有时候也可以用状态转移表表示

### 用图灵机计算函数

NaN

## 线性界限自动机LBA
线性界限自动机(Linear Bounded Automaton)是有限制的图灵机; 它不使用无限纸带，它的纸带有同输入符号数目成正比的空间  

可以证明,LBA 接受上下文有关语言

## 下推自动机PDA
下推自动机(Pushdown Automation)可以看成是一个带有附加下推存储器的有穷自动机,下推存储器是一个堆栈,如下:  
![PDA](PDA0.png)

如果把下推自动机扩展，允许一个有限状态自动机存取两个栈，我们得到一个能力更强的自动机，这个自动机与图灵机等价


## 有穷自动机FA
有穷自动机(Finity Automation)是具有离散输入和输出系统的一种数学模型,它有有限个内部状态.随着信号的输入,内部状态不断地转移

### 定义
有穷自动机(FA)是一个有序五元组$M = <Q, \Sigma, \delta, q_0, F>$, 其中
* $Q$是非空有穷的状态集合
* $\Sigma$是非空有穷的输入字母表
* $\delta$为一个$Q \times \Sigma \to Q$上的映射,是状态转移函数
* $q_0 \in Q$是初始状态
* $F \subseteq Q$是终结状态集合

为了精确描述有穷自动机在输入字符串上的动作,我们推广状态转移函数为$\hat \delta : Q \times \Sigma^\* to Q $如下
> 对任意的$q \in Q, \omega \in \Sigma^\*, a \in \Sigma$都有:  
> $$\hat \delta (q, \epsilon) = q$$  $$\hat \delta (q, \omega a) = \delta (\hat \delta (q, \omega), a)$$  
> 即$\hat \delta (q, \omega)$正好是自动机从状态$q$开始扫描完$\omega$所有符号后所处的状态

### 有穷自动机接受的语言
有穷自动机$M = <Q, \Sigma, \delta, q_0, F>$接受的语言$L(M)$为:
$$L(M) = \lbrace \omega | \omega \in \Sigma^\* , \hat \delta (q_0, \omega) \in F \rbrace$$

由$\delta$定义可知,对于一个确定的状态$q$和输入$a$,输出的次态是唯一的,所以FA在给定字符串上的动作是确定的; 因此上面讲的有穷自动机又叫确定型有穷自动机(DFA)

### 非确定型有穷自动机NFA
若在有穷自动机中,FA在输入字符串上的动作是不确定的,那么这种自动机叫做非确定型有穷自动机

#### 定义
非确定型有穷自动机是一个有序五元组$M = <Q, \Sigma, \delta, q_0, F>$, 其中
* $Q$是非空有穷的状态集合
* $\Sigma$是非空有穷的输入字母表
* $\delta$为一个$Q \times \Sigma \to \rho(Q)$上的映射,$\rho(Q)$表示Q的幂集
* $q_0 \in Q$是初始状态
* $F \subseteq Q$是终结状态集合
这样,$\delta (q, a)$就是一个状态集合,它可以含有一个或多个状态,也可以是空集

类似地,我们将$\delta$推广成$\hat \delta : Q \times \Sigma^\* to \rho(Q)$:
> 对任意的$q \in Q, \omega \in \Sigma^\*, a \in \Sigma$都有:  
> $$\hat \delta (q, \epsilon) = \lbrace q \rbrace$$  $$\hat \delta (q, \omega a) =\bigcup_{r \in \hat \delta (q, \omega)} \hat \delta (r, a)$$
> 此时$\hat \delta (q, \omega)$表示的是从状态$q$开始扫描完$\omega$所有符号后所有可能的结束状态的集合

#### NFA接受的语言
非确定型有穷自动机$M = <Q, \Sigma, \delta, q_0, F>$接受的语言$L(M)$为:
$$L(M) = \lbrace \omega | \omega \in \Sigma^\* , \hat \delta (q_0, \omega) \cap F \ne \emptyset \rbrace$$

#### 性质
* 每一个DFA都可以看成一个特殊的NFA,只要把$\hat \delta (q, \epsilon) = q$看成$\hat \delta (q, \epsilon) = \lbrace q \rbrace$即可  

实际上,相比于DFA,非确定性并没有增加NFA的能力,正如下面所述:
* 对每一个非确定型有穷自动机$M$,都存在一个确定型有穷自动机$M'$,使得$L(M) = L(M')$(证明略)  

这种转换方式在此不做介绍

### 带$\epsilon$转移的非确定型有穷自动机
对NFA稍加推广,不仅对$\Sigma$中的每一个符号都可以有状态转移, 而且在不读入任何符号(或者说读入空串$\epsilon$)的情况下,自动机在某些状态下也可以自动转移到另一个状态, 这样的NFA称为带$\epsilon$转移的NFA

#### 定义
带$\epsilon$转移的非确定型有穷自动机是一个有序五元组$M = <Q, \Sigma, \delta, q_0, F>$, 其中
* $Q$是非空有穷的状态集合
* $\Sigma$是非空有穷的输入字母表
* $\delta$为一个$Q \times (\Sigma \cup \lbrace \epsilon \rbrace) \to \rho(Q)$上的映射,$\rho(Q)$表示Q的幂集
* $q_0 \in Q$是初始状态
* $F \subseteq Q$是终结状态集合

#### 性质
* NFA可以看成是特殊的带$\epsilon$转移的NFA  

实际上,带$\epsilon$转移也没有增加NFA的能力:
* 对每一个带$\epsilon$转移的非确定型有穷自动机$M$,都存在一个非确定型有穷自动机$M'$,使得$L(M) = L(M')$(证明略)  

可见,DFA、NFA、带$\epsilon$转移的NFA这三种自动机模型是等价的

### 有穷自动机和正则文法的等价性
* 模拟是证明两个计算模型等价的主要方法; 用模型A模拟模型B,就是用模型A实现模型B的计算  

可以证明,有穷自动机识别的语言类型恰好是正则语言:
* 对每一个正则语言L,都存在一个带$\epsilon$转移的非确定型有穷自动机$M$使得$L(M) = L$
* 对每一个带$\epsilon$转移的非确定型有穷自动机$M$,都存在一个右线性文法$G$和左线性文法$G'$使得$L(G) = L(G')=L(M)$









