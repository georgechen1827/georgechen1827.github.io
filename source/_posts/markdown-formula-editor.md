---
title: markdown中的公式编辑
categories: [instructions,notes]
tags: [instructions,markdown]
date: 2020-03-04 13:23:34
---

## 基本语法

### 行内公式

正文(inline)中的LaTeX公式用`$...$`定义

例如`$\sum_{i=0}^N\int_{a}^{b}g(t,i)\text{d}t$`

显示为$\sum_{i=0}^N\int_{a}^{b}g(t,i)\text{d}t$

### 行间公式

单独显示(display)的LaTeX公式用`$$...$$`定义，此时公式居中并放大显示  

例如`$$\sum_{i=0}^N\int_{a}^{b}g(t,i)\text{d}t$$`   

显示为$$\sum_{i=0}^N\int_{a}^{b}g(t,i)\text{d}t$$ 

<!--more-->

## 希腊字母
 命令 | 显示 | 命令 | 显示
 :-: | :-: | :-: | :-: 
 \alpha |   $\alpha$    |   A   |   $A$   
 \beta  |   $\beta$ |   B   |   $B$
 \gamma  |   $\gamma$ |   \Gamma   |   $\Gamma$
 \delta  |   $\delta$ |   \Delta   |   $\Delta$
 \epsilon  |   $\epsilon$ |   E   |   $E$
 \zeta  |   $\zeta$ |   Z   |   $Z$
 \eta  |   $\eta$ |   H   |   $H$
 \theta  |   $\theta$ |   \Theta   |   $\Theta$
 \iota  |   $\iota$ |   I   |   $I$
 \kappa  |   $\kappa$ |   K   |   $K$
 \lambda  |   $\lambda$ |   \Lambda   |   $\Lambda$
 \mu |   $\mu$ |   M   |   $M$
 \nu  |   $\nu$ |   N   |   $N$
 \xi  |   $\xi$ |   \Xi   |   $\Xi$
 \omicron  |   $\omicron$ |   O   |   $O$
 \pi  |   $\pi$ |   \Pi   |   $\Pi$
 \rho  |   $\rho$ |   P   |   $P$
 \sigma  |   $\sigma$ |   \Sigma   |   $\Sigma$
 \tau  |   $\tau$ |   T   |   $T$
 \upsilon  |   $\upsilon$ |   Y   |   $Y$
 \phi  |   $\phi$ |   \Phi   |   $\Phi$
 \chi  |   $\chi$ |   X   |   $X$
 \psi |   $\psi$ |   \Psi   |   $\Psi$
 \omega  |   $\omega$ |   \Omega   |   $\Omega$
 
## 上下标
上标和下标分别使用`^`与`_`，例如`$x_i^2$`表示的是$x_i^2$  

默认情况下, 上下标符号仅仅对下一个组起作用。一个组即单个字符或者使用`{..}` 包裹起来的内容。如果使用`$10^10$`表示的是$10^10$;而`$10^{10}$`才是$10^{10}$。同时,大括号还能消除二义性，如`x^5^6` 将得到一个错误，必须使用大括号来界定^的结合性，如`${x^5}^6$`:${x^5}^6$或者`$x^{5^6}$`:$x^{5^6}$。

## 括号

使用原始的`( )`,`[ ]` 即可，如`$(2+3)[4+4]$`:$(2+3)[4+4]$ 
使用\left(或\right)使符号大小与邻近的公式相适应（该语句适用于所有括号类型），如`$\left(\frac{x}{y}\right)$`:$\left(\frac{x}{y}\right)$

以下转载<https://www.jianshu.com/p/8b6fc36035c0>

<!DOCTYPE html>
<html lang="en">
<head>
<title></title>
<style>
body, html {
	width: 100%;
	height: 100%;
}
*, ::after, ::before {
	-webkit-box-sizing: border-box;
	box-sizing: border-box;
}
article, aside, dialog, figcaption, figure, footer, header, hgroup, main, nav, section {
	display: block;
}
._2rhmJa {
	font-weight: 400;
	line-height: 1.8;
	margin-bottom: 20px;
    padding-right: 50px;
}
._3Z3nHf, .ouvJEz {
	background-color: #fff;
	border-radius: 4px;
	margin-bottom: 10px;
}
.ouvJEz {
	padding: 24px;
}
._gp-ck {
	flex-shrink: 0;
	width: 730px;
	margin-bottom: 24px;
	margin-right: 10px;
}
._3VRLsv {
	box-sizing: content-box;
	padding-left: 16px;
    padding-right: 1000px;
	margin-left: auto;
	margin-right: auto;
}
._3VRLsv {
	justify-content: center;
	align-items: flex-start;
	min-height: calc(-66px + 100vh);
}
._3kbg6I {
	background-color: #f9f9f9;
}
body {
	margin: 0;
	color: rgba(0, 0, 0, 0.65);
	font-size: 14px;
	font-family: -apple-system,BlinkMacSystemFont,"Segoe UI","PingFang SC","Hiragino Sans GB","Microsoft YaHei","Helvetica Neue",Helvetica,Arial,sans-serif,"Apple Color Emoji","Segoe UI Emoji","Segoe UI Symbol";
	line-height: 1.5;
	-webkit-font-feature-settings: "tnum","tnum";
	font-feature-settings: "tnum" 1, "tnum" 1;
}
body {
	line-height: 1.4285;
	color: #404040;
	background-color: #fff;
	font-family: -apple-system,BlinkMacSystemFont,"Apple Color Emoji","Segoe UI Emoji","Segoe UI Symbol","Segoe UI","PingFang SC","Hiragino Sans GB","Microsoft YaHei","Helvetica Neue",Helvetica,Arial,sans-serif;
	font-feature-settings: "tnum" 1;
	font-variant: tabular-nums;
}
html {
	font-family: sans-serif;
	line-height: 1.15;
	-webkit-text-size-adjust: 100%;
	-ms-text-size-adjust: 100%;
	-ms-overflow-style: scrollbar;
	-webkit-tap-highlight-color: rgba(0, 0, 0, 0);
}
html {
	--antd-wave-shadow-color: #ec7259;
}
p {
	margin-top: 0px;
	margin-bottom: 1em;
}
._2rhmJa p {
	margin-bottom: 20px;
	word-break: break-word;
}
hr {
	-webkit-box-sizing: content-box;
	box-sizing: content-box;
	height: 0px;
	overflow: visible;
}
._2rhmJa hr {
	margin: 0 0 20px;
	border: 0;
	border-top: 1px solid #eee !important;
}
table {
	border-collapse: collapse;
}
._2rhmJa table {
	width: 100%;
	margin-bottom: 20px;
	border-collapse: collapse;
	border: 1px solid #eee;
	border-left: none;
	word-break: break-word;
}
h1, h2, h3, h4, h5, h6 {
	margin-top: 0px;
	margin-bottom: 0.5em;
	color: rgba(0, 0, 0, 0.85);
	font-weight: 500;
}
b, strong {
	font-weight: bolder;
}
b, h1, h2, h3, h4, h5, h6, strong {
	font-weight: 600;
}
h1, h2, h3, h4, h5, h6 {
	color: #404040;
	text-rendering: optimizelegibility;
}
._2rhmJa h1, ._2rhmJa h2, ._2rhmJa h3, ._2rhmJa h4, ._2rhmJa h5, ._2rhmJa h6 {
	margin-bottom: 16px;
}
._2rhmJa h2 {
	font-size: 24px;
}
dl, ol, ul {
	margin-top: 0px;
	margin-bottom: 1em;
}
ol, ul {
	padding-left: 0px;
	margin: 0;
	list-style: none;
}
ol ol, ol ul, ul ol, ul ul {
	margin-bottom: 0px;
}
._2rhmJa ol, ._2rhmJa ul {
	word-break: break-word;
	margin: 0 0 20px 20px;
}
._2rhmJa ul {
	list-style-type: disc;
}
._2Uzcx_ {
	position: relative;
	overflow: hidden;
}
._2rhmJa h3 {
	font-size: 22px;
}
._2rhmJa ol {
	list-style-type: decimal;
}
._2rhmJa table tr:nth-of-type(2n) {
	background-color: hsla(0, 0%, 70%, 0.15);
}
th {
	text-align: inherit;
}
._2rhmJa table td, ._2rhmJa table th {
	padding: 8px;
	border: 1px solid #eee;
	line-height: 20px;
	vertical-align: middle;
}
a {
	color: #ec7259;
	text-decoration: none;
	background-color: transparent;
	outline: none;
	cursor: pointer;
	-webkit-transition: color .3s;
	transition: color .3s;
	-webkit-text-decoration-skip: objects;
}
[role=button], a, area, button, input:not([type=range]), label, select, summary, textarea {
	-ms-touch-action: manipulation;
	touch-action: manipulation;
}
a {
	color: #0681d0;
}
code, kbd, pre, samp {
	font-size: 1em;
	font-family: "SFMono-Regular",Consolas,"Liberation Mono",Menlo,Courier,monospace;
}
pre {
	margin-top: 0px;
	margin-bottom: 1em;
	overflow: auto;
}
._2rhmJa code {
	padding: 2px 4px;
	border: none;
	vertical-align: middle;
	white-space: pre-wrap;
}
code[class*=language-], pre[class*=language-] {
	color: #ccc;
	background: none;
	font-family: Consolas,Monaco,"Andale Mono","Ubuntu Mono",monospace;
	font-size: 1em;
	text-align: left;
	white-space: pre;
	word-spacing: normal;
	word-break: normal;
	word-wrap: normal;
	line-height: 1.5;
	-moz-tab-size: 4;
	-o-tab-size: 4;
	tab-size: 4;
	-webkit-hyphens: none;
	-moz-hyphens: none;
	-ms-hyphens: none;
	hyphens: none;
}
pre[class*=language-] {
	padding: 1em;
	margin: .5em 0;
	overflow: auto;
}
:not(pre) > code[class*=language-], pre[class*=language-] {
	background: #2d2d2d;
}
._2rhmJa code, ._2rhmJa pre, ._2rhmJa pre[class*=language-] {
	font-family: Consolas,Monaco,"Andale Mono","Ubuntu Mono",monospace;
	font-size: 12px;
}
._2rhmJa pre, ._2rhmJa pre[class*=language-] {
	word-wrap: normal;
	word-break: break-all;
	white-space: pre;
	overflow-x: scroll;
	overscroll-behavior-x: contain;
	margin-top: 0px;
	margin-bottom: 20px;
	border-radius: 4px;
	z-index: 0;
	padding: 1em;
	line-height: 1.5;
	color: #ccc;
	background: #2d2d2d;
}
._2rhmJa :not(pre) code {
	color: #c7254e;
	background-color: #f2f2f2;
}
._2rhmJa table th {
	font-weight: bold;
}
._2rhmJa table thead th {
	vertical-align: middle;
	text-align: inherit;
}
img {
	vertical-align: middle;
	border-style: none;
}
._2rhmJa img {
	max-width: 100%;
}
._2rhmJa [mathimg='1'].math-inline {
	display: inline;
	margin: 0 3px;
	vertical-align: middle;
}
._2rhmJa [mathimg='1'].math-block {
	display: block;
	margin: 1em auto;
}
._2rhmJa [mathimg='1'].math-block, ._2rhmJa [mathimg='1'].math-inline {
	max-width: 100%;
}
button, input, optgroup, select, textarea {
	margin: 0;
	color: inherit;
	font-size: inherit;
	font-family: inherit;
	line-height: inherit;
}
button, input {
	overflow: visible;
}
button, select {
	text-transform: none;
}
.VJbwyy {
	position: absolute;
	top: 6px;
	right: 6px;
	display: flex;
	justify-content: center;
	align-items: center;
	width: 32px;
	height: 24px;
	cursor: pointer;
	font-size: 14px;
	padding: 0;
	border: none;
	border-radius: 6px;
	color: #ccc;
	background-color: hsla(0, 0%, 90%, 0.2);
	box-shadow: 0px 2px 0px 0px rgba(0,0,0,0.25);
	opacity: 0;
	visibility: hidden;
	-webkit-user-select: none;
	-moz-user-select: none;
	-ms-user-select: none;
	user-select: none;
	transition: opacity .2s ease-in-out,visibility .2s ease-in-out;
	z-index: 1;
}
[type=reset], [type=submit], button, html [type=button] {
	-webkit-appearance: button;
}
[role=button], button {
	cursor: pointer;
	-webkit-user-select: none;
	-moz-user-select: none;
	-ms-user-select: none;
	user-select: none;
}
pre[class*=language-].line-numbers {
	position: relative;
	padding-left: 3.8em;
	counter-reset: linenumber;
}
._2rhmJa pre[class*=language-] code, ._2rhmJa pre code {
	padding: 0;
	background-color: transparent;
	color: inherit;
	white-space: pre;
	vertical-align: unset;
}
pre[class*=language-].line-numbers > code {
	position: relative;
	white-space: inherit;
}
.token.atrule, .token.builtin, .token.important, .token.keyword, .token.selector {
	color: #cc99cd;
}
.token.punctuation {
	color: #ccc;
}
.token.entity, .token.operator, .token.url {
	color: #67cdcc;
}
.token.boolean, .token.function, .token.number {
	color: #f08d49;
}
.line-numbers .line-numbers-rows {
	position: absolute;
	pointer-events: none;
	top: 0px;
	font-size: 100%;
	left: -3.8em;
	width: 3em;
	letter-spacing: -1px;
	border-right: 1px solid #999;
	-webkit-user-select: none;
	-moz-user-select: none;
	-ms-user-select: none;
	user-select: none;
}
.line-numbers-rows > span {
	pointer-events: none;
	display: block;
	counter-increment: linenumber;
}
.anticon {
	display: inline-block;
	color: inherit;
	font-style: normal;
	line-height: 0;
	text-align: center;
	text-transform: none;
	vertical-align: -0.12em;
	text-rendering: optimizeLegibility;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
}
.anticon > * {
	line-height: 1;
}
svg:not(:root) {
	overflow: hidden;
}
.anticon svg {
	display: inline-block;
}
._2rhmJa ol li, ._2rhmJa ul li {
	line-height: 30px;
}
.token.class-name, .token.constant, .token.property, .token.symbol {
	color: #f8c555;
}
.token.attr-value, .token.char, .token.regex, .token.string, .token.variable {
	color: #7ec699;
}
._2rhmJa ol li ol, ._2rhmJa ol li ul, ._2rhmJa ul li ol, ._2rhmJa ul li ul {
	margin-top: 16px;
}
</style>
</head>
<body><div id="__next"><div class="_21bLU4 _3kbg6I"><div class="_3VRLsv" role="main"><div class="_gp-ck"><section class="ouvJEz"><article class="_2rhmJa">
<hr>
<table>
<thead>
<tr>
<th style="text-align:center">Author</th>
<th style="text-align:left">shaniadolphin</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:center">e-mail</td>
<td style="text-align:left"><a href="mailto:349948204@qq.com" target="_blank" rel="nofollow">349948204@qq.com</a></td>
</tr>
<tr>
<td style="text-align:center">github</td>
<td style="text-align:left"><a href="https://github.com/shaniadolphin/" target="_blank" rel="nofollow">https://github.com/shaniadolphin/</a></td>
</tr>
</tbody>
</table>
<h3>大括号</h3>
<p>  由于大括号<code>{}</code> 被用于分组，因此需要使用<code>\{</code>和<code>\}</code>表示大括号，也可以使用<code>\lbrace</code> 和<code>\rbrace</code>来表示。如<code>$\{a\*b\}:a\∗b$</code> 或<code>$\lbrace a\*b\rbrace :a\*b$</code> 表示<img class="math-inline" alt="\{a*b\}:a∗b" src="https://math.jianshu.com/math?formula=%5C%7Ba*b%5C%7D%3Aa%E2%88%97b" mathimg="1">。</p>
<h3>尖括号</h3>
<p>  区分于小于号和大于号，使用<code>\langle</code> 和<code>\rangle</code> 表示左尖括号和右尖括号。如<code>$\langle x \rangle$</code> 表示：<img class="math-inline" alt="\langle x \rangle" src="https://math.jianshu.com/math?formula=%5Clangle%20x%20%5Crangle" mathimg="1">。</p>
<h3>上取整</h3>
<p>  使用<code>\lceil</code> 和 <code>\rceil</code> 表示。 如，<code>$\lceil x \rceil$</code>：<img class="math-inline" alt="\lceil x \rceil" src="https://math.jianshu.com/math?formula=%5Clceil%20x%20%5Crceil" mathimg="1">。</p>
<h3>下取整</h3>
<p>  使用<code>\lfloor</code> 和 <code>\rfloor</code> 表示。如，<code>$\lfloor x \rfloor$</code>：<img class="math-inline" alt="\lfloor x \rfloor" src="https://math.jianshu.com/math?formula=%5Clfloor%20x%20%5Crfloor" mathimg="1">。</p>
<h2><strong>求和与积分</strong></h2>
<h3>求和</h3>
<p>  <code>\sum</code> 用来表示求和符号，其下标表示求和下限，上标表示上限。如:<br>
  <code>$\sum_{r=1}^n$</code>表示：<img class="math-inline" alt="\sum_{r=1}^n" src="https://math.jianshu.com/math?formula=%5Csum_%7Br%3D1%7D%5En" mathimg="1">。<br>
  <code>$$\sum_{r=1}^n$$</code>表示：<img class="math-block" alt="\sum_{r=1}^n" src="https://math.jianshu.com/math?formula=%5Csum_%7Br%3D1%7D%5En" mathimg="1"></p>
<h3>积分</h3>
<p>  <code>\int</code> 用来表示积分符号，同样地，其上下标表示积分的上下限。如，<code>$\int_{r=1}^\infty$</code>：<img class="math-inline" alt="\int_{r=1}^\infty" src="https://math.jianshu.com/math?formula=%5Cint_%7Br%3D1%7D%5E%5Cinfty" mathimg="1">。<br>
  多重积分同样使用 <strong>int</strong> ，通过 <strong>i</strong> 的数量表示积分导数：<br>
  <code>$\iint$</code> ：<img class="math-inline" alt="\iint" src="https://math.jianshu.com/math?formula=%5Ciint" mathimg="1"><br>
  <code>$\iiint$</code> ：<img class="math-inline" alt="\iiint" src="https://math.jianshu.com/math?formula=%5Ciiint" mathimg="1"><br>
  <code>$\iiiint$</code> ：<img class="math-inline" alt="\iiiint" src="https://math.jianshu.com/math?formula=%5Ciiiint" mathimg="1"></p>
<h3>连乘</h3>
<p>  <code>$\prod {a+b}$</code>，输出：<img class="math-inline" alt="\prod {a+b}" src="https://math.jianshu.com/math?formula=%5Cprod%20%7Ba%2Bb%7D" mathimg="1">。<br>
  <code>$\prod_{i=1}^{K}$</code>，输出：<img class="math-inline" alt="\prod_{i=1}^{K}" src="https://math.jianshu.com/math?formula=%5Cprod_%7Bi%3D1%7D%5E%7BK%7D" mathimg="1">。<br>
  <code>$$\prod_{i=1}^{K}$$</code>，输出：<img class="math-inline" alt="\prod_{i=1}^{K}" src="https://math.jianshu.com/math?formula=%5Cprod_%7Bi%3D1%7D%5E%7BK%7D" mathimg="1">。</p>
<h3>其他</h3>
<p>  与此类似的符号还有，<br>
  <code>$\prod$</code> ：<img class="math-inline" alt="\prod" src="https://math.jianshu.com/math?formula=%5Cprod" mathimg="1"><br>
  <code>$\bigcup$</code> ：<img class="math-inline" alt="\bigcup" src="https://math.jianshu.com/math?formula=%5Cbigcup" mathimg="1"><br>
  <code>$\bigcap$</code> ：<img class="math-inline" alt="\bigcap" src="https://math.jianshu.com/math?formula=%5Cbigcap" mathimg="1"><br>
  <code>$arg\,\max_{c_k}$</code>：<img class="math-inline" alt="arg\,\max_{c_k}" src="https://math.jianshu.com/math?formula=arg%5C%2C%5Cmax_%7Bc_k%7D" mathimg="1"><br>
  <code>$arg\,\min_{c_k}$</code>：<img class="math-inline" alt="arg\,\min_{c_k}" src="https://math.jianshu.com/math?formula=arg%5C%2C%5Cmin_%7Bc_k%7D" mathimg="1"><br>
  <code>$\mathop {argmin}_{c_k}$</code>：<img class="math-inline" alt="\mathop {argmin}_{c_k}" src="https://math.jianshu.com/math?formula=%5Cmathop%20%7Bargmin%7D_%7Bc_k%7D" mathimg="1"><br>
  <code>$\mathop {argmax}_{c_k}$</code>：<img class="math-inline" alt="\mathop {argmax}_{c_k}" src="https://math.jianshu.com/math?formula=%5Cmathop%20%7Bargmax%7D_%7Bc_k%7D" mathimg="1"><br>
  <code>$\max_{c_k}$</code>：<img class="math-inline" alt="\max_{c_k}" src="https://math.jianshu.com/math?formula=%5Cmax_%7Bc_k%7D" mathimg="1"><br>
  <code>$\min_{c_k}$</code>：<img class="math-inline" alt="\min_{c_k}" src="https://math.jianshu.com/math?formula=%5Cmin_%7Bc_k%7D" mathimg="1"></p>
<h2><strong>分式与根式</strong></h2>
<h3>分式</h3>
<ul>
<li>第一种，使用<code>\frac ab</code>，<code>\frac</code>作用于其后的两个组<code>a</code> ，<code>b</code> ，结果为<img class="math-inline" alt="\frac ab" src="https://math.jianshu.com/math?formula=%5Cfrac%20ab" mathimg="1">。如果你的分子或分母不是单个字符，请使用<code>{..}</code>来分组，比如<code>$\frac {a+c+1}{b+c+2}$</code>表示<img class="math-inline" alt="\frac {a+c+1}{b+c+2}" src="https://math.jianshu.com/math?formula=%5Cfrac%20%7Ba%2Bc%2B1%7D%7Bb%2Bc%2B2%7D" mathimg="1">。</li>
<li>第二种，使用<code>\over</code>来分隔一个组的前后两部分，如<code>{a+1\over b+1}</code>：<img class="math-inline" alt="{a+1\over b+1}" src="https://math.jianshu.com/math?formula=%7Ba%2B1%5Cover%20b%2B1%7D" mathimg="1">
</li>
</ul>
<h3>连分数</h3>
<p>  书写连分数表达式时，请使用<code>\cfrac</code>代替<code>\frac</code>或者<code>\over</code>两者效果对比如下：<br>
  <code>\frac</code> 表示如下：</p>
<div class="_2Uzcx_"><button class="VJbwyy" aria-label="复制代码" type="button"><i class="anticon anticon-copy" aria-label="icon: copy"><svg xmlns="http://www.w3.org/2000/svg" class="" aria-hidden="true" fill="currentColor" viewBox="64 64 896 896" focusable="false" width="1em" height="1em" data-icon="copy"><path d="M 832 64 H 296 c -4.4 0 -8 3.6 -8 8 v 56 c 0 4.4 3.6 8 8 8 h 496 v 688 c 0 4.4 3.6 8 8 8 h 56 c 4.4 0 8 -3.6 8 -8 V 96 c 0 -17.7 -14.3 -32 -32 -32 Z M 704 192 H 192 c -17.7 0 -32 14.3 -32 32 v 530.7 c 0 8.5 3.4 16.6 9.4 22.6 l 173.3 173.3 c 2.2 2.2 4.7 4 7.4 5.5 v 1.9 h 4.2 c 3.5 1.3 7.2 2 11 2 H 704 c 17.7 0 32 -14.3 32 -32 V 224 c 0 -17.7 -14.3 -32 -32 -32 Z M 350 856.2 L 263.9 770 H 350 v 86.2 Z M 664 888 H 414 V 746 c 0 -22.1 -17.9 -40 -40 -40 H 232 V 264 h 432 v 624 Z" /></svg></i></button><pre class="line-numbers  language-ruby"><code class="  language-ruby"><span class="token variable">$$x</span><span class="token operator">=</span>a_0 <span class="token operator">+</span> \frac <span class="token punctuation">{</span><span class="token number">1</span><span class="token operator">^</span><span class="token number">2</span><span class="token punctuation">}</span><span class="token punctuation">{</span>a_1 <span class="token operator">+</span> \frac <span class="token punctuation">{</span><span class="token number">2</span><span class="token operator">^</span><span class="token number">2</span><span class="token punctuation">}</span><span class="token punctuation">{</span>a_2 <span class="token operator">+</span> \frac <span class="token punctuation">{</span><span class="token number">3</span><span class="token operator">^</span><span class="token number">2</span><span class="token punctuation">}</span><span class="token punctuation">{</span>a_3 <span class="token operator">+</span> \frac <span class="token punctuation">{</span><span class="token number">4</span><span class="token operator">^</span><span class="token number">2</span><span class="token punctuation">}</span><span class="token punctuation">{</span>a_4 <span class="token operator">+</span> <span class="token punctuation">.</span><span class="token punctuation">.</span><span class="token punctuation">.</span><span class="token punctuation">}</span><span class="token punctuation">}</span><span class="token punctuation">}</span><span class="token punctuation">}</span>$$
<span class="line-numbers-rows" aria-hidden="true"><span></span></span></code></pre></div>
<p>  显示如下：<br>
<img class="math-block" alt="x=a_0 + \frac {1^2}{a_1 + \frac {2^2}{a_2 + \frac {3^2}{a_3 + \frac {4^2}{a_4 + ...}}}}" src="https://math.jianshu.com/math?formula=x%3Da_0%20%2B%20%5Cfrac%20%7B1%5E2%7D%7Ba_1%20%2B%20%5Cfrac%20%7B2%5E2%7D%7Ba_2%20%2B%20%5Cfrac%20%7B3%5E2%7D%7Ba_3%20%2B%20%5Cfrac%20%7B4%5E2%7D%7Ba_4%20%2B%20...%7D%7D%7D%7D" mathimg="1"><br>
  <code>\cfrac</code> 表示如下：</p>
<div class="_2Uzcx_"><button class="VJbwyy" aria-label="复制代码" type="button"><i class="anticon anticon-copy" aria-label="icon: copy"><svg xmlns="http://www.w3.org/2000/svg" class="" aria-hidden="true" fill="currentColor" viewBox="64 64 896 896" focusable="false" width="1em" height="1em" data-icon="copy"><path d="M 832 64 H 296 c -4.4 0 -8 3.6 -8 8 v 56 c 0 4.4 3.6 8 8 8 h 496 v 688 c 0 4.4 3.6 8 8 8 h 56 c 4.4 0 8 -3.6 8 -8 V 96 c 0 -17.7 -14.3 -32 -32 -32 Z M 704 192 H 192 c -17.7 0 -32 14.3 -32 32 v 530.7 c 0 8.5 3.4 16.6 9.4 22.6 l 173.3 173.3 c 2.2 2.2 4.7 4 7.4 5.5 v 1.9 h 4.2 c 3.5 1.3 7.2 2 11 2 H 704 c 17.7 0 32 -14.3 32 -32 V 224 c 0 -17.7 -14.3 -32 -32 -32 Z M 350 856.2 L 263.9 770 H 350 v 86.2 Z M 664 888 H 414 V 746 c 0 -22.1 -17.9 -40 -40 -40 H 232 V 264 h 432 v 624 Z" /></svg></i></button><pre class="line-numbers  language-ruby"><code class="  language-ruby"><span class="token variable">$$x</span><span class="token operator">=</span>a_0 <span class="token operator">+</span> \cfrac <span class="token punctuation">{</span><span class="token number">1</span><span class="token operator">^</span><span class="token number">2</span><span class="token punctuation">}</span><span class="token punctuation">{</span>a_1 <span class="token operator">+</span> \cfrac <span class="token punctuation">{</span><span class="token number">2</span><span class="token operator">^</span><span class="token number">2</span><span class="token punctuation">}</span><span class="token punctuation">{</span>a_2 <span class="token operator">+</span> \cfrac <span class="token punctuation">{</span><span class="token number">3</span><span class="token operator">^</span><span class="token number">2</span><span class="token punctuation">}</span><span class="token punctuation">{</span>a_3 <span class="token operator">+</span> \cfrac <span class="token punctuation">{</span><span class="token number">4</span><span class="token operator">^</span><span class="token number">2</span><span class="token punctuation">}</span><span class="token punctuation">{</span>a_4 <span class="token operator">+</span> <span class="token punctuation">.</span><span class="token punctuation">.</span><span class="token punctuation">.</span><span class="token punctuation">}</span><span class="token punctuation">}</span><span class="token punctuation">}</span><span class="token punctuation">}</span>$$
<span class="line-numbers-rows" aria-hidden="true"><span></span></span></code></pre></div>
<p>  显示如下：<br>
<img class="math-block" alt="x=a_0 + \cfrac {1^2}{a_1 + \cfrac {2^2}{a_2 + \cfrac {3^2}{a_3 + \cfrac {4^2}{a_4 + ...}}}}" src="https://math.jianshu.com/math?formula=x%3Da_0%20%2B%20%5Ccfrac%20%7B1%5E2%7D%7Ba_1%20%2B%20%5Ccfrac%20%7B2%5E2%7D%7Ba_2%20%2B%20%5Ccfrac%20%7B3%5E2%7D%7Ba_3%20%2B%20%5Ccfrac%20%7B4%5E2%7D%7Ba_4%20%2B%20...%7D%7D%7D%7D" mathimg="1"></p>
<h3>根式</h3>
<p>  根式使用<code>\sqrt</code> 来表示。<br>
  如开4次方：<code>$\sqrt[4]{\frac xy}$</code> ：<img class="math-inline" alt="\sqrt[4]{\frac xy}" src="https://math.jianshu.com/math?formula=%5Csqrt%5B4%5D%7B%5Cfrac%20xy%7D" mathimg="1">。<br>
  开平方：<code>$\sqrt {a+b}$</code>：<img class="math-inline" alt="\sqrt {a+b}" src="https://math.jianshu.com/math?formula=%5Csqrt%20%7Ba%2Bb%7D" mathimg="1">。</p>
<h2><strong>多行表达式</strong></h2>
<h3>分类表达式</h3>
<p>  定义函数的时候经常需要分情况给出表达式，使用<code>\begin{cases}…\end{cases}</code> 。其中：</p>
<ul>
<li>  使用<code>\\</code> 来分类，</li>
<li>  使用<code>&amp;</code> 指示需要对齐的位置，</li>
<li>  使用<code>\</code> +<code>空格</code>表示空格。</li>
</ul>
<div class="_2Uzcx_"><button class="VJbwyy" aria-label="复制代码" type="button"><i class="anticon anticon-copy" aria-label="icon: copy"><svg xmlns="http://www.w3.org/2000/svg" class="" aria-hidden="true" fill="currentColor" viewBox="64 64 896 896" focusable="false" width="1em" height="1em" data-icon="copy"><path d="M 832 64 H 296 c -4.4 0 -8 3.6 -8 8 v 56 c 0 4.4 3.6 8 8 8 h 496 v 688 c 0 4.4 3.6 8 8 8 h 56 c 4.4 0 8 -3.6 8 -8 V 96 c 0 -17.7 -14.3 -32 -32 -32 Z M 704 192 H 192 c -17.7 0 -32 14.3 -32 32 v 530.7 c 0 8.5 3.4 16.6 9.4 22.6 l 173.3 173.3 c 2.2 2.2 4.7 4 7.4 5.5 v 1.9 h 4.2 c 3.5 1.3 7.2 2 11 2 H 704 c 17.7 0 32 -14.3 32 -32 V 224 c 0 -17.7 -14.3 -32 -32 -32 Z M 350 856.2 L 263.9 770 H 350 v 86.2 Z M 664 888 H 414 V 746 c 0 -22.1 -17.9 -40 -40 -40 H 232 V 264 h 432 v 624 Z" /></svg></i></button><pre class="line-numbers  language-ruby"><code class="  language-ruby">$$
f<span class="token punctuation">(</span>n<span class="token punctuation">)</span>
\<span class="token keyword">begin</span><span class="token punctuation">{</span>cases<span class="token punctuation">}</span>
\cfrac n2<span class="token punctuation">,</span> <span class="token operator">&amp;</span><span class="token keyword">if</span>\ n\ is\ even\\
<span class="token number">3</span>n <span class="token operator">+</span> <span class="token number">1</span><span class="token punctuation">,</span> <span class="token operator">&amp;</span><span class="token keyword">if</span>\  n\ is\ odd
\<span class="token keyword">end</span><span class="token punctuation">{</span>cases<span class="token punctuation">}</span>
$$
<span class="line-numbers-rows" aria-hidden="true"><span></span><span></span><span></span><span></span><span></span><span></span><span></span></span></code></pre></div>
<p>  表示:<br>
<img class="math-block" alt="f(n) \begin{cases} \cfrac n2, &amp;if\ n\ is\ even\\ 3n + 1, &amp;if\ n\ is\ odd \end{cases}" src="https://math.jianshu.com/math?formula=f(n)%20%5Cbegin%7Bcases%7D%20%5Ccfrac%20n2%2C%20%26if%5C%20n%5C%20is%5C%20even%5C%5C%203n%20%2B%201%2C%20%26if%5C%20n%5C%20is%5C%20odd%20%5Cend%7Bcases%7D" mathimg="1"></p>
<div class="_2Uzcx_"><button class="VJbwyy" aria-label="复制代码" type="button"><i class="anticon anticon-copy" aria-label="icon: copy"><svg xmlns="http://www.w3.org/2000/svg" class="" aria-hidden="true" fill="currentColor" viewBox="64 64 896 896" focusable="false" width="1em" height="1em" data-icon="copy"><path d="M 832 64 H 296 c -4.4 0 -8 3.6 -8 8 v 56 c 0 4.4 3.6 8 8 8 h 496 v 688 c 0 4.4 3.6 8 8 8 h 56 c 4.4 0 8 -3.6 8 -8 V 96 c 0 -17.7 -14.3 -32 -32 -32 Z M 704 192 H 192 c -17.7 0 -32 14.3 -32 32 v 530.7 c 0 8.5 3.4 16.6 9.4 22.6 l 173.3 173.3 c 2.2 2.2 4.7 4 7.4 5.5 v 1.9 h 4.2 c 3.5 1.3 7.2 2 11 2 H 704 c 17.7 0 32 -14.3 32 -32 V 224 c 0 -17.7 -14.3 -32 -32 -32 Z M 350 856.2 L 263.9 770 H 350 v 86.2 Z M 664 888 H 414 V 746 c 0 -22.1 -17.9 -40 -40 -40 H 232 V 264 h 432 v 624 Z" /></svg></i></button><pre class="line-numbers  language-ruby"><code class="  language-ruby">$$
<span class="token constant">L</span><span class="token punctuation">(</span><span class="token constant">Y</span><span class="token punctuation">,</span>f<span class="token punctuation">(</span><span class="token constant">X</span><span class="token punctuation">)</span><span class="token punctuation">)</span> <span class="token operator">=</span>
\<span class="token keyword">begin</span><span class="token punctuation">{</span>cases<span class="token punctuation">}</span>
<span class="token number">0</span><span class="token punctuation">,</span> <span class="token operator">&amp;</span> \text<span class="token punctuation">{</span><span class="token constant">Y</span> <span class="token operator">=</span> f<span class="token punctuation">(</span><span class="token constant">X</span><span class="token punctuation">)</span><span class="token punctuation">}</span>  \\
<span class="token number">1</span><span class="token punctuation">,</span> <span class="token operator">&amp;</span> \text<span class="token punctuation">{</span><span class="token constant">Y</span> $\neq$ f<span class="token punctuation">(</span><span class="token constant">X</span><span class="token punctuation">)</span><span class="token punctuation">}</span>
\<span class="token keyword">end</span><span class="token punctuation">{</span>cases<span class="token punctuation">}</span>
$$
<span class="line-numbers-rows" aria-hidden="true"><span></span><span></span><span></span><span></span><span></span><span></span><span></span></span></code></pre></div>
<p>  表示:<br>
<img class="math-block" alt="L(Y,f(X)) = \begin{cases} 0, &amp; \text{Y = f(X)} \\ 1, &amp; \text{Y $\neq$ f(X)} \end{cases}" src="https://math.jianshu.com/math?formula=L(Y%2Cf(X))%20%3D%20%5Cbegin%7Bcases%7D%200%2C%20%26%20%5Ctext%7BY%20%3D%20f(X)%7D%20%5C%5C%201%2C%20%26%20%5Ctext%7BY%20%24%5Cneq%24%20f(X)%7D%20%5Cend%7Bcases%7D" mathimg="1"><br>
  如果想分类之间的垂直间隔变大，可以使用<code>\\[2ex]</code> 代替<code>\\</code> 来分隔不同的情况。(<code>3ex,4ex</code> 也可以用，<code>1ex</code> 相当于原始距离）。如下所示：</p>
<div class="_2Uzcx_"><button class="VJbwyy" aria-label="复制代码" type="button"><i class="anticon anticon-copy" aria-label="icon: copy"><svg xmlns="http://www.w3.org/2000/svg" class="" aria-hidden="true" fill="currentColor" viewBox="64 64 896 896" focusable="false" width="1em" height="1em" data-icon="copy"><path d="M 832 64 H 296 c -4.4 0 -8 3.6 -8 8 v 56 c 0 4.4 3.6 8 8 8 h 496 v 688 c 0 4.4 3.6 8 8 8 h 56 c 4.4 0 8 -3.6 8 -8 V 96 c 0 -17.7 -14.3 -32 -32 -32 Z M 704 192 H 192 c -17.7 0 -32 14.3 -32 32 v 530.7 c 0 8.5 3.4 16.6 9.4 22.6 l 173.3 173.3 c 2.2 2.2 4.7 4 7.4 5.5 v 1.9 h 4.2 c 3.5 1.3 7.2 2 11 2 H 704 c 17.7 0 32 -14.3 32 -32 V 224 c 0 -17.7 -14.3 -32 -32 -32 Z M 350 856.2 L 263.9 770 H 350 v 86.2 Z M 664 888 H 414 V 746 c 0 -22.1 -17.9 -40 -40 -40 H 232 V 264 h 432 v 624 Z" /></svg></i></button><pre class="line-numbers  language-ruby"><code class="  language-ruby">$$
<span class="token constant">L</span><span class="token punctuation">(</span><span class="token constant">Y</span><span class="token punctuation">,</span>f<span class="token punctuation">(</span><span class="token constant">X</span><span class="token punctuation">)</span><span class="token punctuation">)</span> <span class="token operator">=</span>
\<span class="token keyword">begin</span><span class="token punctuation">{</span>cases<span class="token punctuation">}</span>
<span class="token number">0</span><span class="token punctuation">,</span> <span class="token operator">&amp;</span> \text<span class="token punctuation">{</span><span class="token constant">Y</span> <span class="token operator">=</span> f<span class="token punctuation">(</span><span class="token constant">X</span><span class="token punctuation">)</span><span class="token punctuation">}</span> \\<span class="token punctuation">[</span><span class="token number">5</span>ex<span class="token punctuation">]</span>
<span class="token number">1</span><span class="token punctuation">,</span> <span class="token operator">&amp;</span> \text<span class="token punctuation">{</span><span class="token constant">Y</span> $\neq$ f<span class="token punctuation">(</span><span class="token constant">X</span><span class="token punctuation">)</span><span class="token punctuation">}</span>
\<span class="token keyword">end</span><span class="token punctuation">{</span>cases<span class="token punctuation">}</span>
$$
<span class="line-numbers-rows" aria-hidden="true"><span></span><span></span><span></span><span></span><span></span><span></span><span></span></span></code></pre></div>
<p>  表示：<br>
<img class="math-block" alt="L(Y,f(X)) = \begin{cases} 0, &amp; \text{Y = f(X)} \\[5ex] 1, &amp; \text{Y $\neq$ f(X)} \end{cases}" src="https://math.jianshu.com/math?formula=L(Y%2Cf(X))%20%3D%20%5Cbegin%7Bcases%7D%200%2C%20%26%20%5Ctext%7BY%20%3D%20f(X)%7D%20%5C%5C%5B5ex%5D%201%2C%20%26%20%5Ctext%7BY%20%24%5Cneq%24%20f(X)%7D%20%5Cend%7Bcases%7D" mathimg="1"></p>
<h3>多行表达式</h3>
<p>  有时候需要将一行公式分多行进行显示。</p>
<div class="_2Uzcx_"><button class="VJbwyy" aria-label="复制代码" type="button"><i class="anticon anticon-copy" aria-label="icon: copy"><svg xmlns="http://www.w3.org/2000/svg" class="" aria-hidden="true" fill="currentColor" viewBox="64 64 896 896" focusable="false" width="1em" height="1em" data-icon="copy"><path d="M 832 64 H 296 c -4.4 0 -8 3.6 -8 8 v 56 c 0 4.4 3.6 8 8 8 h 496 v 688 c 0 4.4 3.6 8 8 8 h 56 c 4.4 0 8 -3.6 8 -8 V 96 c 0 -17.7 -14.3 -32 -32 -32 Z M 704 192 H 192 c -17.7 0 -32 14.3 -32 32 v 530.7 c 0 8.5 3.4 16.6 9.4 22.6 l 173.3 173.3 c 2.2 2.2 4.7 4 7.4 5.5 v 1.9 h 4.2 c 3.5 1.3 7.2 2 11 2 H 704 c 17.7 0 32 -14.3 32 -32 V 224 c 0 -17.7 -14.3 -32 -32 -32 Z M 350 856.2 L 263.9 770 H 350 v 86.2 Z M 664 888 H 414 V 746 c 0 -22.1 -17.9 -40 -40 -40 H 232 V 264 h 432 v 624 Z" /></svg></i></button><pre class="line-numbers  language-ruby"><code class="  language-ruby">$$
\<span class="token keyword">begin</span><span class="token punctuation">{</span>equation<span class="token punctuation">}</span>\<span class="token keyword">begin</span><span class="token punctuation">{</span>split<span class="token punctuation">}</span> 
a<span class="token operator">&amp;</span><span class="token operator">=</span>b<span class="token operator">+</span>c<span class="token operator">-</span>d \\ 
<span class="token operator">&amp;</span>\quad <span class="token operator">+</span>e<span class="token operator">-</span>f\\ 
<span class="token operator">&amp;</span><span class="token operator">=</span>g<span class="token operator">+</span>h\\ 
<span class="token operator">&amp;</span> <span class="token operator">=</span>i 
\<span class="token keyword">end</span><span class="token punctuation">{</span>split<span class="token punctuation">}</span>\<span class="token keyword">end</span><span class="token punctuation">{</span>equation<span class="token punctuation">}</span>
$$
<span class="line-numbers-rows" aria-hidden="true"><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span></span></code></pre></div>
<p>  表示：<br>
<img class="math-block" alt="\begin{equation}\begin{split} a&amp;=b+c-d \\ &amp;\quad +e-f\\ &amp;=g+h\\ &amp; =i \end{split}\end{equation}" src="https://math.jianshu.com/math?formula=%5Cbegin%7Bequation%7D%5Cbegin%7Bsplit%7D%20a%26%3Db%2Bc-d%20%5C%5C%20%26%5Cquad%20%2Be-f%5C%5C%20%26%3Dg%2Bh%5C%5C%20%26%20%3Di%20%5Cend%7Bsplit%7D%5Cend%7Bequation%7D" mathimg="1"><br>
  其中<code>begin{equation}</code> 表示开始方程，<code>end{equation}</code> 表示方程结束；<code>begin{split}</code> 表示开始多行公式，<code>end{split}</code> 表示结束；公式中用<code>\\</code> 表示回车到下一行，<code>&amp;</code> 表示对齐的位置。</p>
<h3>方程组</h3>
<p>  使用<code>\begin{array}...\end{array}</code> 与<code>\left \{</code> 与<code>\right.</code> 配合表示方程组:</p>
<div class="_2Uzcx_"><button class="VJbwyy" aria-label="复制代码" type="button"><i class="anticon anticon-copy" aria-label="icon: copy"><svg xmlns="http://www.w3.org/2000/svg" class="" aria-hidden="true" fill="currentColor" viewBox="64 64 896 896" focusable="false" width="1em" height="1em" data-icon="copy"><path d="M 832 64 H 296 c -4.4 0 -8 3.6 -8 8 v 56 c 0 4.4 3.6 8 8 8 h 496 v 688 c 0 4.4 3.6 8 8 8 h 56 c 4.4 0 8 -3.6 8 -8 V 96 c 0 -17.7 -14.3 -32 -32 -32 Z M 704 192 H 192 c -17.7 0 -32 14.3 -32 32 v 530.7 c 0 8.5 3.4 16.6 9.4 22.6 l 173.3 173.3 c 2.2 2.2 4.7 4 7.4 5.5 v 1.9 h 4.2 c 3.5 1.3 7.2 2 11 2 H 704 c 17.7 0 32 -14.3 32 -32 V 224 c 0 -17.7 -14.3 -32 -32 -32 Z M 350 856.2 L 263.9 770 H 350 v 86.2 Z M 664 888 H 414 V 746 c 0 -22.1 -17.9 -40 -40 -40 H 232 V 264 h 432 v 624 Z" /></svg></i></button><pre class="line-numbers  language-ruby"><code class="  language-ruby">$$
\left \<span class="token punctuation">{</span> 
\<span class="token keyword">begin</span><span class="token punctuation">{</span>array<span class="token punctuation">}</span><span class="token punctuation">{</span>c<span class="token punctuation">}</span>
a_1x<span class="token operator">+</span>b_1y<span class="token operator">+</span>c_1z<span class="token operator">=</span>d_1 \\ 
a_2x<span class="token operator">+</span>b_2y<span class="token operator">+</span>c_2z<span class="token operator">=</span>d_2 \\ 
a_3x<span class="token operator">+</span>b_3y<span class="token operator">+</span>c_3z<span class="token operator">=</span>d_3
\<span class="token keyword">end</span><span class="token punctuation">{</span>array<span class="token punctuation">}</span>
\right<span class="token punctuation">.</span>
$$
<span class="line-numbers-rows" aria-hidden="true"><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span></span></code></pre></div>
<p>  表示：<br>
<img class="math-block" alt="\left \{ \begin{array}{c} a_1x+b_1y+c_1z=d_1 \\ a_2x+b_2y+c_2z=d_2 \\ a_3x+b_3y+c_3z=d_3 \end{array} \right." src="https://math.jianshu.com/math?formula=%5Cleft%20%5C%7B%20%5Cbegin%7Barray%7D%7Bc%7D%20a_1x%2Bb_1y%2Bc_1z%3Dd_1%20%5C%5C%20a_2x%2Bb_2y%2Bc_2z%3Dd_2%20%5C%5C%20a_3x%2Bb_3y%2Bc_3z%3Dd_3%20%5Cend%7Barray%7D%20%5Cright." mathimg="1"><br>
  注意：通常MathJax通过内部策略自己管理公式内部的空间，因此<code>a…b</code> 与<code>a…….b</code> （<code>.</code>表示空格）都会显示为<code>ab</code> 。可以通过在<code>ab</code> 间加入<code>\</code> ,增加些许间隙，<code>\;</code> 增加较宽的间隙，<code>\quad</code>  与<code>\qquad</code> 会增加更大的间隙。</p>
<h2><strong>特殊函数与符号</strong></h2>
<h3>三角函数</h3>
<p>  <code>\snx$</code> : <img class="math-inline" alt="sinx" src="https://math.jianshu.com/math?formula=sinx" mathimg="1"><br>
  <code>\arctanx</code> : <img class="math-inline" alt="arctanx" src="https://math.jianshu.com/math?formula=arctanx" mathimg="1"></p>
<h3>比较运算符</h3>
<p>  小于(<code>\lt</code> )：<img class="math-inline" alt="\lt" src="https://math.jianshu.com/math?formula=%5Clt" mathimg="1"><br>
  大于(<code>\gt</code> )：<img class="math-inline" alt="\gt" src="https://math.jianshu.com/math?formula=%5Cgt" mathimg="1"><br>
  小于等于(<code>\le</code> )：<img class="math-inline" alt="\le" src="https://math.jianshu.com/math?formula=%5Cle" mathimg="1"><br>
  大于等于(<code>\ge</code> )：<img class="math-inline" alt="\ge" src="https://math.jianshu.com/math?formula=%5Cge" mathimg="1"><br>
  不等于(<code>\ne</code> ) : <img class="math-inline" alt="\ne" src="https://math.jianshu.com/math?formula=%5Cne" mathimg="1"><br>
  可以在这些运算符前面加上<code>\not</code> ，如<code>\not\lt</code> : <img class="math-inline" alt="\not\lt`" src="https://math.jianshu.com/math?formula=%5Cnot%5Clt%60" mathimg="1"></p>
<h3>集合关系与运算</h3>
<p>  并集(<code>\cup</code> ): <img class="math-inline" alt="\cup" src="https://math.jianshu.com/math?formula=%5Ccup" mathimg="1"><br>
  交集(<code>\cap</code> ): <img class="math-inline" alt="\cap" src="https://math.jianshu.com/math?formula=%5Ccap" mathimg="1"><br>
  差集(<code>\setminus</code> ): <img class="math-inline" alt="\setminus" src="https://math.jianshu.com/math?formula=%5Csetminus" mathimg="1"><br>
  子集(<code>\subset</code> ): <img class="math-inline" alt="\subset" src="https://math.jianshu.com/math?formula=%5Csubset" mathimg="1"><br>
  子集(<code>\subseteq</code> ): <img class="math-inline" alt="\subseteq" src="https://math.jianshu.com/math?formula=%5Csubseteq" mathimg="1"><br>
  非子集(<code>\subsetneq</code> ): <img class="math-inline" alt="\subsetneq" src="https://math.jianshu.com/math?formula=%5Csubsetneq" mathimg="1"><br>
  父集(<code>\supset</code> ): <img class="math-inline" alt="\supset" src="https://math.jianshu.com/math?formula=%5Csupset" mathimg="1"><br>
  属于(<code>\in</code> ): <img class="math-inline" alt="\in" src="https://math.jianshu.com/math?formula=%5Cin" mathimg="1"><br>
  不属于(<code>\notin</code> ): <img class="math-inline" alt="\notin" src="https://math.jianshu.com/math?formula=%5Cnotin" mathimg="1"><br>
  空集(<code>\emptyset</code> ): <img class="math-inline" alt="\emptyset" src="https://math.jianshu.com/math?formula=%5Cemptyset" mathimg="1"><br>
  空(<code>\varnothing</code> ): <img class="math-inline" alt="\varnothing" src="https://math.jianshu.com/math?formula=%5Cvarnothing" mathimg="1"></p>
<h3>排列</h3>
<p>  <code>\binom{n+1}{2k}</code> : <img class="math-inline" alt="\binom{n+1}{2k}" src="https://math.jianshu.com/math?formula=%5Cbinom%7Bn%2B1%7D%7B2k%7D" mathimg="1"><br>
  <code>{n+1 \choose 2k}</code> : <img class="math-inline" alt="{n+1 \choose 2k}" src="https://math.jianshu.com/math?formula=%7Bn%2B1%20%5Cchoose%202k%7D" mathimg="1"></p>
<h3>箭头</h3>
<p>  (<code>\to</code> ):<img class="math-inline" alt="\to" src="https://math.jianshu.com/math?formula=%5Cto" mathimg="1"><br>
  (<code>\rightarrow</code> ): <img class="math-inline" alt="\rightarrow" src="https://math.jianshu.com/math?formula=%5Crightarrow" mathimg="1"><br>
  (<code>\leftarrow</code> ): <img class="math-inline" alt="\leftarrow" src="https://math.jianshu.com/math?formula=%5Cleftarrow" mathimg="1"><br>
  (<code>\Rightarrow</code> ): <img class="math-inline" alt="\Rightarrow" src="https://math.jianshu.com/math?formula=%5CRightarrow" mathimg="1"><br>
  (<code>\Leftarrow</code> ): <img class="math-inline" alt="\Leftarrow" src="https://math.jianshu.com/math?formula=%5CLeftarrow" mathimg="1"><br>
  (<code>\mapsto</code> ): <img class="math-inline" alt="\mapsto" src="https://math.jianshu.com/math?formula=%5Cmapsto" mathimg="1"></p>
<h3>逻辑运算符</h3>
<p>  (<code>\land</code> ): <img class="math-inline" alt="\land" src="https://math.jianshu.com/math?formula=%5Cland" mathimg="1"><br>
  (<code>\lor</code> ): <img class="math-inline" alt="\lor" src="https://math.jianshu.com/math?formula=%5Clor" mathimg="1"><br>
  (<code>\lnot</code> ): <img class="math-inline" alt="\lnot" src="https://math.jianshu.com/math?formula=%5Clnot" mathimg="1"><br>
  (<code>\forall</code> ): <img class="math-inline" alt="\forall" src="https://math.jianshu.com/math?formula=%5Cforall" mathimg="1"><br>
  (<code>\exists</code> ): <img class="math-inline" alt="\exists" src="https://math.jianshu.com/math?formula=%5Cexists" mathimg="1"><br>
  (<code>\top</code> ): <img class="math-inline" alt="\top" src="https://math.jianshu.com/math?formula=%5Ctop" mathimg="1"><br>
  (<code>\bot</code> ): <img class="math-inline" alt="\bot" src="https://math.jianshu.com/math?formula=%5Cbot" mathimg="1"><br>
  (<code>\vdash</code> ): <img class="math-inline" alt="\vdash" src="https://math.jianshu.com/math?formula=%5Cvdash" mathimg="1"><br>
  (<code>\vDash</code> ): <img class="math-inline" alt="\vDash" src="https://math.jianshu.com/math?formula=%5CvDash" mathimg="1"></p>
<h3>操作符</h3>
<p>  (<code>\star</code> ): <img class="math-inline" alt="\star" src="https://math.jianshu.com/math?formula=%5Cstar" mathimg="1"><br>
  (<code>\ast</code> ): <img class="math-inline" alt="\ast" src="https://math.jianshu.com/math?formula=%5Cast" mathimg="1"><br>
  (<code>\oplus</code> ): <img class="math-inline" alt="\oplus" src="https://math.jianshu.com/math?formula=%5Coplus" mathimg="1"><br>
  (<code>\circ</code> ): <img class="math-inline" alt="\circ" src="https://math.jianshu.com/math?formula=%5Ccirc" mathimg="1"><br>
  (<code>\bullet</code> ): <img class="math-inline" alt="\bullet" src="https://math.jianshu.com/math?formula=%5Cbullet" mathimg="1"></p>
<h3>等于</h3>
<p>  (<code>\approx</code> ): <img class="math-inline" alt="\approx" src="https://math.jianshu.com/math?formula=%5Capprox" mathimg="1"><br>
  (<code>\sim</code> ): <img class="math-inline" alt="\sim" src="https://math.jianshu.com/math?formula=%5Csim" mathimg="1"><br>
  (<code>\equiv</code> ): <img class="math-inline" alt="\equiv" src="https://math.jianshu.com/math?formula=%5Cequiv" mathimg="1"><br>
  (<code>\prec</code> ): <img class="math-inline" alt="\prec" src="https://math.jianshu.com/math?formula=%5Cprec" mathimg="1"></p>
<h3>范围</h3>
<p>  (<code>\infty</code> ): <img class="math-inline" alt="\infty" src="https://math.jianshu.com/math?formula=%5Cinfty" mathimg="1"><br>
  (<code>\aleph_o</code> ): <img class="math-inline" alt="\aleph_o" src="https://math.jianshu.com/math?formula=%5Caleph_o" mathimg="1"><br>
  (<code>\nabla</code> ): <img class="math-inline" alt="\nabla" src="https://math.jianshu.com/math?formula=%5Cnabla" mathimg="1"><br>
  (<code>\Im</code> ): <img class="math-inline" alt="\Im" src="https://math.jianshu.com/math?formula=%5CIm" mathimg="1"><br>
  (<code>\Re</code> ): <img class="math-inline" alt="\Re" src="https://math.jianshu.com/math?formula=%5CRe" mathimg="1"></p>
<h3>模运算</h3>
<p>  (<code>\pmod</code> ): <img class="math-inline" alt="b \pmod n" src="https://math.jianshu.com/math?formula=b%20%5Cpmod%20n" mathimg="1"><br>
  如<code>a \equiv b \pmod n</code> : <img class="math-inline" alt="a \equiv b \pmod n" src="https://math.jianshu.com/math?formula=a%20%5Cequiv%20b%20%5Cpmod%20n" mathimg="1"></p>
<h3>点</h3>
<p>  (<code>\ldots</code> ): <img class="math-inline" alt="\ldots" src="https://math.jianshu.com/math?formula=%5Cldots" mathimg="1"><br>
  (<code>\cdots</code> ): <img class="math-inline" alt="\cdots" src="https://math.jianshu.com/math?formula=%5Ccdots" mathimg="1"><br>
  (<code>\cdot</code> ): <img class="math-inline" alt="\cdot" src="https://math.jianshu.com/math?formula=%5Ccdot" mathimg="1"><br>
  其区别是点的位置不同，<code>\ldots</code> 位置稍低，<code>\cdots</code> 位置居中。</p>
<div class="_2Uzcx_"><button class="VJbwyy" aria-label="复制代码" type="button"><i class="anticon anticon-copy" aria-label="icon: copy"><svg xmlns="http://www.w3.org/2000/svg" class="" aria-hidden="true" fill="currentColor" viewBox="64 64 896 896" focusable="false" width="1em" height="1em" data-icon="copy"><path d="M 832 64 H 296 c -4.4 0 -8 3.6 -8 8 v 56 c 0 4.4 3.6 8 8 8 h 496 v 688 c 0 4.4 3.6 8 8 8 h 56 c 4.4 0 8 -3.6 8 -8 V 96 c 0 -17.7 -14.3 -32 -32 -32 Z M 704 192 H 192 c -17.7 0 -32 14.3 -32 32 v 530.7 c 0 8.5 3.4 16.6 9.4 22.6 l 173.3 173.3 c 2.2 2.2 4.7 4 7.4 5.5 v 1.9 h 4.2 c 3.5 1.3 7.2 2 11 2 H 704 c 17.7 0 32 -14.3 32 -32 V 224 c 0 -17.7 -14.3 -32 -32 -32 Z M 350 856.2 L 263.9 770 H 350 v 86.2 Z M 664 888 H 414 V 746 c 0 -22.1 -17.9 -40 -40 -40 H 232 V 264 h 432 v 624 Z" /></svg></i></button><pre class="line-numbers  language-ruby"><code class="  language-ruby">$$
\<span class="token keyword">begin</span><span class="token punctuation">{</span>equation<span class="token punctuation">}</span>
a_1<span class="token operator">+</span>a_2<span class="token operator">+</span>\ldots<span class="token operator">+</span>a_n \\ 
a_1<span class="token operator">+</span>a_2<span class="token operator">+</span>\cdots<span class="token operator">+</span>a_n
\<span class="token keyword">end</span><span class="token punctuation">{</span>equation<span class="token punctuation">}</span>
$$
<span class="line-numbers-rows" aria-hidden="true"><span></span><span></span><span></span><span></span><span></span><span></span></span></code></pre></div>
<p>  表示：<br>
<img class="math-block" alt="\begin{equation} a_1+a_2+\ldots+a_n \\ a_1+a_2+\cdots+a_n \end{equation}" src="https://math.jianshu.com/math?formula=%5Cbegin%7Bequation%7D%20a_1%2Ba_2%2B%5Cldots%2Ba_n%20%5C%5C%20a_1%2Ba_2%2B%5Ccdots%2Ba_n%20%5Cend%7Bequation%7D" mathimg="1"></p>
<h2><strong>顶部符号</strong></h2>
<p>  对于单字符，<code>\hat x</code> ：<img class="math-inline" alt="\hat x" src="https://math.jianshu.com/math?formula=%5Chat%20x" mathimg="1"><br>
  多字符可以使用<code>\widehat {xy}</code> ：<img class="math-inline" alt="\widehat {xy}" src="https://math.jianshu.com/math?formula=%5Cwidehat%20%7Bxy%7D" mathimg="1"><br>
  类似的还有:<br>
  (<code>\overline x</code> ): <img class="math-inline" alt="\overline x" src="https://math.jianshu.com/math?formula=%5Coverline%20x" mathimg="1"><br>
  矢量(<code>\vec</code> ): <img class="math-inline" alt="\vec x" src="https://math.jianshu.com/math?formula=%5Cvec%20x" mathimg="1"><br>
  向量(<code>\overrightarrow {xy}</code> ): <img class="math-inline" alt="\overrightarrow {xy}" src="https://math.jianshu.com/math?formula=%5Coverrightarrow%20%7Bxy%7D" mathimg="1"><br>
  (<code>\dot x</code> ): <img class="math-inline" alt="\dot x" src="https://math.jianshu.com/math?formula=%5Cdot%20x" mathimg="1"><br>
  (<code>\ddot x</code> ): <img class="math-inline" alt="\ddot x" src="https://math.jianshu.com/math?formula=%5Cddot%20x" mathimg="1"><br>
  (<code>\dot {\dot x}</code> ): <img class="math-inline" alt="\dot {\dot x}" src="https://math.jianshu.com/math?formula=%5Cdot%20%7B%5Cdot%20x%7D" mathimg="1"></p>
<h2><strong>表格</strong></h2>
<p>  使用<code>\begin{array}{列样式}…\end{array}</code> 这样的形式来创建表格，列样式可以是<code>clr</code> 表示居中，左，右对齐，还可以使用<code>|</code> 表示一条竖线。表格中各行使用<code>\\</code> 分隔，各列使用<code>&amp;</code> 分隔。使用<code>\hline</code> 在本行前加入一条直线。 例如:</p>
<div class="_2Uzcx_"><button class="VJbwyy" aria-label="复制代码" type="button"><i class="anticon anticon-copy" aria-label="icon: copy"><svg xmlns="http://www.w3.org/2000/svg" class="" aria-hidden="true" fill="currentColor" viewBox="64 64 896 896" focusable="false" width="1em" height="1em" data-icon="copy"><path d="M 832 64 H 296 c -4.4 0 -8 3.6 -8 8 v 56 c 0 4.4 3.6 8 8 8 h 496 v 688 c 0 4.4 3.6 8 8 8 h 56 c 4.4 0 8 -3.6 8 -8 V 96 c 0 -17.7 -14.3 -32 -32 -32 Z M 704 192 H 192 c -17.7 0 -32 14.3 -32 32 v 530.7 c 0 8.5 3.4 16.6 9.4 22.6 l 173.3 173.3 c 2.2 2.2 4.7 4 7.4 5.5 v 1.9 h 4.2 c 3.5 1.3 7.2 2 11 2 H 704 c 17.7 0 32 -14.3 32 -32 V 224 c 0 -17.7 -14.3 -32 -32 -32 Z M 350 856.2 L 263.9 770 H 350 v 86.2 Z M 664 888 H 414 V 746 c 0 -22.1 -17.9 -40 -40 -40 H 232 V 264 h 432 v 624 Z" /></svg></i></button><pre class="line-numbers  language-ruby"><code class="  language-ruby">$$
\<span class="token keyword">begin</span><span class="token punctuation">{</span>array<span class="token punctuation">}</span><span class="token punctuation">{</span>c<span class="token operator">|</span>lcr<span class="token punctuation">}</span>
n <span class="token operator">&amp;</span> \text<span class="token punctuation">{</span><span class="token constant">Left</span><span class="token punctuation">}</span> <span class="token operator">&amp;</span> \text<span class="token punctuation">{</span><span class="token constant">Center</span><span class="token punctuation">}</span> <span class="token operator">&amp;</span> \text<span class="token punctuation">{</span><span class="token constant">Right</span><span class="token punctuation">}</span> \\
\hline
<span class="token number">1</span> <span class="token operator">&amp;</span> <span class="token number">0.24</span> <span class="token operator">&amp;</span> <span class="token number">1</span> <span class="token operator">&amp;</span> <span class="token number">125</span> \\
<span class="token number">2</span> <span class="token operator">&amp;</span> <span class="token operator">-</span><span class="token number">1</span> <span class="token operator">&amp;</span> <span class="token number">189</span> <span class="token operator">&amp;</span> <span class="token operator">-</span><span class="token number">8</span> \\
<span class="token number">3</span> <span class="token operator">&amp;</span> <span class="token operator">-</span><span class="token number">20</span> <span class="token operator">&amp;</span> <span class="token number">2000</span> <span class="token operator">&amp;</span> <span class="token number">1</span><span class="token operator">+</span><span class="token number">10</span>i \\
\<span class="token keyword">end</span><span class="token punctuation">{</span>array<span class="token punctuation">}</span>
$$
<span class="line-numbers-rows" aria-hidden="true"><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span></span></code></pre></div>
<p>  得到：<br>
<img class="math-block" alt="\begin{array}{c|lcr} n &amp; \text{Left} &amp; \text{Center} &amp; \text{Right} \\ \hline 1 &amp; 0.24 &amp; 1 &amp; 125 \\ 2 &amp; -1 &amp; 189 &amp; -8 \\ 3 &amp; -20 &amp; 2000 &amp; 1+10i \\ \end{array}" src="https://math.jianshu.com/math?formula=%5Cbegin%7Barray%7D%7Bc%7Clcr%7D%20n%20%26%20%5Ctext%7BLeft%7D%20%26%20%5Ctext%7BCenter%7D%20%26%20%5Ctext%7BRight%7D%20%5C%5C%20%5Chline%201%20%26%200.24%20%26%201%20%26%20125%20%5C%5C%202%20%26%20-1%20%26%20189%20%26%20-8%20%5C%5C%203%20%26%20-20%20%26%202000%20%26%201%2B10i%20%5C%5C%20%5Cend%7Barray%7D" mathimg="1"></p>
<h2><strong>矩阵</strong></h2>
<h3>基本内容</h3>
<p>  使用<code>\begin{matrix}…\end{matrix}</code> 这样的形式来表示矩阵，在<code>\begin</code> 与<code>\end</code> 之间加入矩阵中的元素即可。矩阵的行之间使用<code>\\</code> 分隔，列之间使用<code>&amp;</code> 分隔，例如:</p>
<div class="_2Uzcx_"><button class="VJbwyy" aria-label="复制代码" type="button"><i class="anticon anticon-copy" aria-label="icon: copy"><svg xmlns="http://www.w3.org/2000/svg" class="" aria-hidden="true" fill="currentColor" viewBox="64 64 896 896" focusable="false" width="1em" height="1em" data-icon="copy"><path d="M 832 64 H 296 c -4.4 0 -8 3.6 -8 8 v 56 c 0 4.4 3.6 8 8 8 h 496 v 688 c 0 4.4 3.6 8 8 8 h 56 c 4.4 0 8 -3.6 8 -8 V 96 c 0 -17.7 -14.3 -32 -32 -32 Z M 704 192 H 192 c -17.7 0 -32 14.3 -32 32 v 530.7 c 0 8.5 3.4 16.6 9.4 22.6 l 173.3 173.3 c 2.2 2.2 4.7 4 7.4 5.5 v 1.9 h 4.2 c 3.5 1.3 7.2 2 11 2 H 704 c 17.7 0 32 -14.3 32 -32 V 224 c 0 -17.7 -14.3 -32 -32 -32 Z M 350 856.2 L 263.9 770 H 350 v 86.2 Z M 664 888 H 414 V 746 c 0 -22.1 -17.9 -40 -40 -40 H 232 V 264 h 432 v 624 Z" /></svg></i></button><pre class="line-numbers  language-ruby"><code class="  language-ruby">$$
\<span class="token keyword">begin</span><span class="token punctuation">{</span>matrix<span class="token punctuation">}</span>
<span class="token number">1</span> <span class="token operator">&amp;</span> x <span class="token operator">&amp;</span> x<span class="token operator">^</span><span class="token number">2</span> \\
<span class="token number">1</span> <span class="token operator">&amp;</span> y <span class="token operator">&amp;</span> y<span class="token operator">^</span><span class="token number">2</span> \\
<span class="token number">1</span> <span class="token operator">&amp;</span> z <span class="token operator">&amp;</span> z<span class="token operator">^</span><span class="token number">2</span> \\
\<span class="token keyword">end</span><span class="token punctuation">{</span>matrix<span class="token punctuation">}</span>
$$
<span class="line-numbers-rows" aria-hidden="true"><span></span><span></span><span></span><span></span><span></span><span></span><span></span></span></code></pre></div>
<p>  得到：<br>
<img class="math-block" alt="\begin{matrix} 1 &amp; x &amp; x^2 \\ 1 &amp; y &amp; y^2 \\ 1 &amp; z &amp; z^2 \\ \end{matrix}" src="https://math.jianshu.com/math?formula=%5Cbegin%7Bmatrix%7D%201%20%26%20x%20%26%20x%5E2%20%5C%5C%201%20%26%20y%20%26%20y%5E2%20%5C%5C%201%20%26%20z%20%26%20z%5E2%20%5C%5C%20%5Cend%7Bmatrix%7D" mathimg="1"></p>
<h3>括号</h3>
<p>  如果要对矩阵加括号，可以像上文中提到的一样，使用<code>\left</code> 与<code>\right</code> 配合表示括号符号。也可以使用特殊的<code>matrix</code> 。即替换<code>\begin{matrix}…\end{matrix}</code> 中<code>matrix</code> 为<code>pmatrix</code> ，<code>bmatrix</code> ，<code>Bmatrix</code> ，<code>vmatrix</code> , <code>Vmatrix</code> 。</p>
<ol>
<li>pmatrix<code>$\begin{pmatrix}1 &amp; 2 \\ 3 &amp; 4\\ \end{pmatrix}$</code> : <img class="math-inline" alt="\begin{pmatrix}1 &amp; 2 \\ 3 &amp; 4\\ \end{pmatrix}" src="https://math.jianshu.com/math?formula=%5Cbegin%7Bpmatrix%7D1%20%26%202%20%5C%5C%203%20%26%204%5C%5C%20%5Cend%7Bpmatrix%7D" mathimg="1">
</li>
<li>bmatrix<code>$\begin{bmatrix}1 &amp; 2 \\ 3 &amp; 4\\ \end{bmatrix}$</code> : <img class="math-inline" alt="\begin{bmatrix}1 &amp; 2 \\ 3 &amp; 4\\ \end{bmatrix}" src="https://math.jianshu.com/math?formula=%5Cbegin%7Bbmatrix%7D1%20%26%202%20%5C%5C%203%20%26%204%5C%5C%20%5Cend%7Bbmatrix%7D" mathimg="1">
</li>
<li>Bmatrix<code>$\begin{Bmatrix}1 &amp; 2 \\ 3 &amp; 4\\ \end{Bmatrix}$</code> : <img class="math-inline" alt="\begin{Bmatrix}1 &amp; 2 \\ 3 &amp; 4\\ \end{Bmatrix}" src="https://math.jianshu.com/math?formula=%5Cbegin%7BBmatrix%7D1%20%26%202%20%5C%5C%203%20%26%204%5C%5C%20%5Cend%7BBmatrix%7D" mathimg="1">
</li>
<li>vmatrix<code>$\begin{vmatrix}1 &amp; 2 \\ 3 &amp; 4\\ \end{vmatrix}$</code> : <img class="math-inline" alt="\begin{vmatrix}1 &amp; 2 \\ 3 &amp; 4\\ \end{vmatrix}" src="https://math.jianshu.com/math?formula=%5Cbegin%7Bvmatrix%7D1%20%26%202%20%5C%5C%203%20%26%204%5C%5C%20%5Cend%7Bvmatrix%7D" mathimg="1">
</li>
<li>Vmatrix<code>$\begin{Vmatrix}1 &amp; 2 \\ 3 &amp; 4\\ \end{Vmatrix}$</code> : <img class="math-inline" alt="\begin{Vmatrix}1 &amp; 2 \\ 3 &amp; 4\\ \end{Vmatrix}" src="https://math.jianshu.com/math?formula=%5Cbegin%7BVmatrix%7D1%20%26%202%20%5C%5C%203%20%26%204%5C%5C%20%5Cend%7BVmatrix%7D" mathimg="1">
</li>
</ol>
<h3>元素省略</h3>
<p>  可以使用<code>\cdots</code> ：⋯，<code>\ddots</code>：⋱ ，<code>\vdots</code>：⋮ 来省略矩阵中的元素，如：</p>
<div class="_2Uzcx_"><button class="VJbwyy" aria-label="复制代码" type="button"><i class="anticon anticon-copy" aria-label="icon: copy"><svg xmlns="http://www.w3.org/2000/svg" class="" aria-hidden="true" fill="currentColor" viewBox="64 64 896 896" focusable="false" width="1em" height="1em" data-icon="copy"><path d="M 832 64 H 296 c -4.4 0 -8 3.6 -8 8 v 56 c 0 4.4 3.6 8 8 8 h 496 v 688 c 0 4.4 3.6 8 8 8 h 56 c 4.4 0 8 -3.6 8 -8 V 96 c 0 -17.7 -14.3 -32 -32 -32 Z M 704 192 H 192 c -17.7 0 -32 14.3 -32 32 v 530.7 c 0 8.5 3.4 16.6 9.4 22.6 l 173.3 173.3 c 2.2 2.2 4.7 4 7.4 5.5 v 1.9 h 4.2 c 3.5 1.3 7.2 2 11 2 H 704 c 17.7 0 32 -14.3 32 -32 V 224 c 0 -17.7 -14.3 -32 -32 -32 Z M 350 856.2 L 263.9 770 H 350 v 86.2 Z M 664 888 H 414 V 746 c 0 -22.1 -17.9 -40 -40 -40 H 232 V 264 h 432 v 624 Z" /></svg></i></button><pre class="line-numbers  language-ruby"><code class="  language-ruby">$$
\<span class="token keyword">begin</span><span class="token punctuation">{</span>pmatrix<span class="token punctuation">}</span>
<span class="token number">1</span><span class="token operator">&amp;</span>a_1<span class="token operator">&amp;</span>a_1<span class="token operator">^</span><span class="token number">2</span><span class="token operator">&amp;</span>\cdots<span class="token operator">&amp;</span>a_1<span class="token operator">^</span>n\\
<span class="token number">1</span><span class="token operator">&amp;</span>a_2<span class="token operator">&amp;</span>a_2<span class="token operator">^</span><span class="token number">2</span><span class="token operator">&amp;</span>\cdots<span class="token operator">&amp;</span>a_2<span class="token operator">^</span>n\\
\vdots<span class="token operator">&amp;</span>\vdots<span class="token operator">&amp;</span>\vdots<span class="token operator">&amp;</span>\ddots<span class="token operator">&amp;</span>\vdots\\
<span class="token number">1</span><span class="token operator">&amp;</span>a_m<span class="token operator">&amp;</span>a_m<span class="token operator">^</span><span class="token number">2</span><span class="token operator">&amp;</span>\cdots<span class="token operator">&amp;</span>a_m<span class="token operator">^</span>n\\
\<span class="token keyword">end</span><span class="token punctuation">{</span>pmatrix<span class="token punctuation">}</span>
$$
<span class="line-numbers-rows" aria-hidden="true"><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span></span></code></pre></div>
<p>  表示：<br>
<img class="math-block" alt="\begin{pmatrix} 1&amp;a_1&amp;a_1^2&amp;\cdots&amp;a_1^n\\ 1&amp;a_2&amp;a_2^2&amp;\cdots&amp;a_2^n\\ \vdots&amp;\vdots&amp;\vdots&amp;\ddots&amp;\vdots\\ 1&amp;a_m&amp;a_m^2&amp;\cdots&amp;a_m^n\\ \end{pmatrix}" src="https://math.jianshu.com/math?formula=%5Cbegin%7Bpmatrix%7D%201%26a_1%26a_1%5E2%26%5Ccdots%26a_1%5En%5C%5C%201%26a_2%26a_2%5E2%26%5Ccdots%26a_2%5En%5C%5C%20%5Cvdots%26%5Cvdots%26%5Cvdots%26%5Cddots%26%5Cvdots%5C%5C%201%26a_m%26a_m%5E2%26%5Ccdots%26a_m%5En%5C%5C%20%5Cend%7Bpmatrix%7D" mathimg="1"></p>
<h3>增广矩阵</h3>
<p>  增广矩阵需要使用前面的表格中使用到的<code>\begin{array} ... \end{array}</code> 来实现。</p>
<div class="_2Uzcx_"><button class="VJbwyy" aria-label="复制代码" type="button"><i class="anticon anticon-copy" aria-label="icon: copy"><svg xmlns="http://www.w3.org/2000/svg" class="" aria-hidden="true" fill="currentColor" viewBox="64 64 896 896" focusable="false" width="1em" height="1em" data-icon="copy"><path d="M 832 64 H 296 c -4.4 0 -8 3.6 -8 8 v 56 c 0 4.4 3.6 8 8 8 h 496 v 688 c 0 4.4 3.6 8 8 8 h 56 c 4.4 0 8 -3.6 8 -8 V 96 c 0 -17.7 -14.3 -32 -32 -32 Z M 704 192 H 192 c -17.7 0 -32 14.3 -32 32 v 530.7 c 0 8.5 3.4 16.6 9.4 22.6 l 173.3 173.3 c 2.2 2.2 4.7 4 7.4 5.5 v 1.9 h 4.2 c 3.5 1.3 7.2 2 11 2 H 704 c 17.7 0 32 -14.3 32 -32 V 224 c 0 -17.7 -14.3 -32 -32 -32 Z M 350 856.2 L 263.9 770 H 350 v 86.2 Z M 664 888 H 414 V 746 c 0 -22.1 -17.9 -40 -40 -40 H 232 V 264 h 432 v 624 Z" /></svg></i></button><pre class="line-numbers  language-swift"><code class="  language-swift">$$
\<span class="token keyword">left</span><span class="token punctuation">[</span>  \begin<span class="token punctuation">{</span>array<span class="token punctuation">}</span>  <span class="token punctuation">{</span>c c <span class="token operator">|</span> c<span class="token punctuation">}</span> <span class="token operator">%</span>这里的c表示数组中元素对其方式：c居中、r右对齐、l左对齐，竖线表示<span class="token number">2</span>、<span class="token number">3</span>列间插入竖线
<span class="token number">1</span> <span class="token operator">&amp;</span> <span class="token number">2</span> <span class="token operator">&amp;</span> <span class="token number">3</span> \\
\hline <span class="token operator">%</span>插入横线，如果去掉\hline就是增广矩阵
<span class="token number">4</span> <span class="token operator">&amp;</span> <span class="token number">5</span> <span class="token operator">&amp;</span> <span class="token number">6</span>
\end<span class="token punctuation">{</span>array<span class="token punctuation">}</span>  \<span class="token keyword">right</span><span class="token punctuation">]</span>
$$
<span class="line-numbers-rows" aria-hidden="true"><span></span><span></span><span></span><span></span><span></span><span></span><span></span></span></code></pre></div>
<p>显示为：<br>
<img class="math-block" alt="\left[ \begin{array} {c c | c} 1 &amp; 2 &amp; 3 \\ \hline 4 &amp; 5 &amp; 6 \end{array} \right]" src="https://math.jianshu.com/math?formula=%5Cleft%5B%20%5Cbegin%7Barray%7D%20%7Bc%20c%20%7C%20c%7D%201%20%26%202%20%26%203%20%5C%5C%20%5Chline%204%20%26%205%20%26%206%20%5Cend%7Barray%7D%20%5Cright%5D" mathimg="1"></p>
<h2><strong>公式标记与引用</strong></h2>
<p>  使用<code>\tag{yourtag}</code> 来标记公式，如果想在之后引用该公式，则还需要加上<code>\label{yourlabel}</code> 在<code>\tag</code> 之后，如<code>$$a = x^2 - y^3 \tag{1}\label{1}$$</code> 显示为：<br>
<img class="math-block" alt="a := x^2 - y^3 \tag{1}\label{311}" src="https://math.jianshu.com/math?formula=a%20%3A%3D%20x%5E2%20-%20y%5E3%20%5Ctag%7B1%7D%5Clabel%7B311%7D" mathimg="1"><br>
  如果不需要被引用，只使用<code>\tag{yourtag}</code> ，<code>$$x+y=z\tag{1.1}$$</code>显示为：<br>
<img class="math-block" alt="x+y=z\tag{1.1}" src="https://math.jianshu.com/math?formula=x%2By%3Dz%5Ctag%7B1.1%7D" mathimg="1"><br>
  <code>\tab{yourtab}</code> 中的内容用于显示公式后面的标记。公式之间通过<code>\label{}</code> 设置的内容来引用。为了引用公式，可以使用<code>\eqref{yourlabel}</code> ，如<code>$$a + y^3 \stackrel{\eqref{1}}= x^2$$</code> 显示为：<br>
<img class="math-block" alt="a + y^3 \stackrel{\eqref{1}}= x^2" src="https://math.jianshu.com/math?formula=a%20%2B%20y%5E3%20%5Cstackrel%7B%5Ceqref%7B1%7D%7D%3D%20x%5E2" mathimg="1"></p>
<p>或者使用<code>\ref{yourlabel}</code> 不带括号引用，如<code>$$a + y^3 \stackrel{\ref{111}}= x^2$$</code> 显示为:<br>
<img class="math-block" alt="a + y^3 \stackrel{\ref{1}}= x^2" src="https://math.jianshu.com/math?formula=a%20%2B%20y%5E3%20%5Cstackrel%7B%5Cref%7B1%7D%7D%3D%20x%5E2" mathimg="1"></p>
<h2><strong>字体</strong></h2>
<h3>黑板粗体字</h3>
<p>此字体经常用来表示代表实数、整数、有理数、复数的大写字母。<br>
<code>$\mathbb ABCDEF$</code>：<img class="math-inline" alt="\mathbb ABCDEF" src="https://math.jianshu.com/math?formula=%5Cmathbb%20ABCDEF" mathimg="1"><br>
<code>$\Bbb ABCDEF$</code>：<img class="math-inline" alt="\Bbb ABCDEF" src="https://math.jianshu.com/math?formula=%5CBbb%20ABCDEF" mathimg="1"></p>
<h3>黑体字</h3>
<p><code>$\mathbf ABCDEFGHIJKLMNOPQRSTUVWXYZ$</code> :<img class="math-inline" alt="\mathbf ABCDEFGHIJKLMNOPQRSTUVWXYZ" src="https://math.jianshu.com/math?formula=%5Cmathbf%20ABCDEFGHIJKLMNOPQRSTUVWXYZ" mathimg="1"><br>
<code>$\mathbf abcdefghijklmnopqrstuvwxyz$</code> :<img class="math-inline" alt="\mathbf abcdefghijklmnopqrstuvwxyz" src="https://math.jianshu.com/math?formula=%5Cmathbf%20abcdefghijklmnopqrstuvwxyz" mathimg="1"></p>
<h3>打印机字体</h3>
<p><code>$\mathtt ABCDEFGHIJKLMNOPQRSTUVWXYZ$</code> :<img class="math-inline" alt="\mathtt ABCDEFGHIJKLMNOPQRSTUVWXYZ" src="https://math.jianshu.com/math?formula=%5Cmathtt%20ABCDEFGHIJKLMNOPQRSTUVWXYZ" mathimg="1"></p>
<h2><strong>参考文档</strong></h2>
<table>
<thead>
<tr>
<th>#</th>
<th>链接地址</th>
<th>文档名称</th>
</tr>
</thead>
<tbody>
<tr>
<td>1</td>
<td><code>blog.csdn.net/dabokele/article/details/79577072</code></td>
<td><a href="https://blog.csdn.net/dabokele/article/details/79577072" target="_blank" rel="nofollow">Mathjax公式教程</a></td>
</tr>
<tr>
<td>2</td>
<td><code>blog.csdn.net/ethmery/article/details/50670297</code></td>
<td><a href="https://blog.csdn.net/ethmery/article/details/50670297" target="_blank" rel="nofollow">基本数学公式语法</a></td>
</tr>
<tr>
<td>3</td>
<td><code>blog.csdn.net/lilongsy/article/details/79378620</code></td>
<td><a href="https://blog.csdn.net/lilongsy/article/details/79378620" target="_blank" rel="nofollow">常用数学符号的LaTeX表示方法</a></td>
</tr>
<tr>
<td>4</td>
<td><code>www.mathjax.org</code></td>
<td><a href="https://www.mathjax.org/" target="_blank" rel="nofollow">Beautiful math in all browsers</a></td>
</tr>
</tbody>
</table>
</article></section></div></div></div></div></body>
</html>











