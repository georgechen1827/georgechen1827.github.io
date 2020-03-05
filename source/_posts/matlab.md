---
title: matlab常用语法
categories: notes
tags: [matlab,learning]
date: 2020-02-09 17:10:30
---

仅作随笔用,不完善不严谨

### 变量 符号 数组 矩阵

#### 变量

```matlab
<var> = <expression>
```

预定义变量   
```matlab
pi  % 圆周率
inf % 又Inf,无穷大
nan % 又NaN,不定值
eps % 浮点数运算相对精度,无穷小
i   % 又j,虚部单位
ans % 上一次运算结果
```

变量存储 读取 清除  
```matlab
save [filename.mat] [var1] [var2] ...
load <filename.mat> [var1] [var2] ...
clear [var1] [var2]
```

相关命令
```matlab
who % 显示工作空间中的所有变量  
whos    % 查看工作空间中变量的详细属性 
realmin % 最小可用正实数
realmax % 最大可用正实数
```

<!--more-->

#### 符号 符号表达式

```matlab
syms [symbol1] <symbol2> <symbol3> ...  % 创建多个符号变量, 相当于symbol1 = sym('symbol'); symbol2 = sym('symbol2'); ...
[symbol] = sym([symbol/value/symbolexpression])  % 用符号/数值/表达式来创建符号变量/常量/表达式
```

相关函数  
```matlab
findsym(expression [, N])   % 查找符号表达式中的[离x最近的N个]符号变量
subs(expression, symbol1, symbol2)  % 在表达式中用s2替换s1
```

#### 数组 矩阵

```matlab
[matrix] = [row1 ; row2 ; ... ]
[row] = [sym1 sym2 ...] % row = start: step: end
[matrix](n) = value % 元素赋值
[matrix] = [matrix ; matrix2]   % 矩阵列拼接
[matrix] = [matrix matrix2] % 矩阵行拼接
```

相关操作
```matlab
A(i1 : step : i2, j1 : step : j2)   % 矩阵切片
.* ./ .^    % 点乘点除点幂乘
```

### 函数

#### 基本函数

```matlab
sin、cos、tan、cot、sec、csc、…
asin、acos、atan、acot、asec、acsc、…
exp、log、log2、log10、sqrt
abs、conj、real、imag
rank、det、inv、eig、lu、qr、svd
diag、triu、tril、expm
```

相关命令  
```matlab
findsym(expr)   % 按字母顺序列出符号表达式 expr 中的所有符号变量
findsym(expr, N)    % 按顺序列出 expr 中离 x 最近的 N 个符号变量
nargin  % 所用函数的输入变量数目
nargout % 所用函数的输出变量数目
```

####　运算函数

```matlab
factor(f)   % 因式分解或质因数分解
expand(f)   % 函数展开
taylor(f,x,a)   % f关于符号x在a处进行5项泰勒展开
collect(f,v)    % f对(默认变量)v进行合并同类项
simplify(f) % 对f化简函数
numden(f)   % 函数化简 -> [N,D] N为分子,D为分母
horner(f)   % 多项式转嵌套多项式 x(...x(x+i)+j)+k
```

```matlab
limit(fun,x,x0 [, 'left'/'right'])  % 在fun中对符号x在x0处求极限
int(f [, v, a, b])  % 在f中对(默认)变量[v][在区间(a,b)上]的(不)定积分
symsum(f, v, a, b)  % 在v=a,a+1....b上对f(v)进行求和
solve(f,v)  % 求方程(组)关于指定自变量的解
y=dsolve(eq1, eq2, ..., cond1, cond2, ..., v)   % 微分方程eq1,eq2...在cond1,cond2...为初值条件下自变量v的解 -> 输出解y,若无显式函数,则输出[x,y]
finverse(f,v)   % f关于(默认变量)v的反函数
```

#### 多项式函数

```matlab
p = [a1, a2, a3, a4 ...]    % 多项式降幂系数的行向量表示
r = roots(p)    % 求出多项式为0的根
p = poly(r) % 通过多项式为0的根求出多项式
c = conv(a,b)   % 多项式相乘
[q, r] = deconv(c, b)   % 多项式相除
d = polyder(a)  % 微分多项式
n = polyval(a, 2)   % 多项式函数求值
p = polyfit(x,y,n)  % 在x, y样本点向量下求出一个n阶多项式的拟合p
[a,Jm] = lsqcurvefit(Fun,a0,x,y)    % 最小二乘曲线拟合,Fun为原函数，x,y 为原始输入数据,a0为最优化初值，a为最小二乘系数，Jm为目标
yi = interp1(x, y, xi, 'method')    % 一维插值计算
zi = interp2(x，y，z，xi，yi，'method')  % 二维插值计算
```

#### 作图函数

参考<https://www.cnblogs.com/ileanj1998/p/9060664.html>

```matlab
plot(x,y)   % x 为向量, y为x的函数或者同长度向量
xlabel('x') ylabel('y') % 坐标轴信息]
```

### 其他技巧 

* 若不想在屏幕上输出结果，可以在语句最后加分号  
* 如果语句很长，可用续行符 “…”（三个点）续行,续行符的前面最好留一个空格
* Matlab 的命令记忆功能：上下箭头键  
* 命令补全功能： Tab 键   
* 用 Esc 键 删除命令行
