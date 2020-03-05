---
title: 使用termux在安卓系统下搭建hexo-github博客编写环境
categories: instructions
tags: [instructions,hexo] 
date: 2020-02-07 14:46:16
---

在hexo已经部署到github的情况下，本文将记录如何把自己的移动设备(安卓手机、平板)变成可以编辑并上传博客的平台。  

关于如何在github上搭建hexo，详见<https://zhuanlan.zhihu.com/p/44213627>  
注意：使用多终端更新博客之前，请确保自己的博客系统在github上面同时有编译前、后两个分支，多终端更新方法可参考<https://keyanbu.club/2020/02/05/guide/>

本博文使用matepad pro在安卓环境下编写完成。  

<!--more-->

### 思路  

由于安卓系统下没有直接支持git及hexo的软件，我们使用termux来虚拟出一个linux环境，在终端中安装git及相关包，使用vim或安卓的相关文本编辑器(我用的920编辑器)来编写博文，用termux终端同步博客。  

相关问题：
* 使用termux的pkg安装nodejs时可能会出现与npm版本不兼容的情况，安装nodejs-lts可解决。
* 使用在使用hexo generate生成博客时可能会出现网页排版错误，尚未解决。  


以下所有操作都相对小白，懂的可以直接略过  

### 环境配置  

除了安装termux之外，其他操作几乎和电脑上是一样的

* 安装termux

``` bash
# 自己去网上找安装包安装，这里不说了
# 安装好之后进入termux，应该是一个显示如下的终端

Welcome to Termux!

Wiki:            https://wiki.termux.com
Community forum: https://termux.com/community
Gitter chat:     https://gitter.im/termux/termux
IRC channel:     #termux on freenode

Working with packages:

 * Search packages:   pkg search <query>
 * Install a package: pkg install <package>
 * Upgrade packages:  pkg upgrade

Subscribing to additional repositories:

 * Root:     pkg install root-repo
 * Unstable: pkg install unstable-repo
 * X11:      pkg install x11-repo

Report issues at https://termux.com/issues

$

```

* 安装git

``` bash
$ pkg install git
```

* 设置git全局邮箱和用户名

```bash
$ git config --global user.name "yourname"
$ git config --global user.email "youremail"
```

* 设置ssh key  

这里得先安openssh  
```bash
$ pkg install openssh
```
然后生成ssh key  
```bash
$ ssh-keygen -t rsa -C "youremail"
# 然后一路默认回车即可
```
这里注意，生成的ssh_key路径是在隐藏目录home/.ssh下的，需要进入˜/.ssh用vim打开id_rsa.pub复制公钥。
```bash
# 此时是默认home路径
$ cd .ssh    # 切换到.ssh目录
$ vim id_rsa.pub
# 此时进入vim编辑器，屏幕上显示内容应该和如下类似

ssh-rsa AAAADAQABAAABgQC8uwcEZdQna+zv/HTa2W4I
AvqiNyKxgVdi07ce8hRTpb/lejdVK5rux7jOkWM00Pl73
7qTKXAgWkgVckflinjfd6bxgOEA0ZUYRcFjuMYNccOdWO
XDfmX0w4GYaKhGG5RMsWxVsNSfoskjYpCs1fiSTvM49Y6
FWsEzyXaQ46VWedZJKqEhVPoAtZOEmNOi0krsqymzfjZj
7/iVzuZiFP/zN5itPJXHvYMTA0OzDiPo3qHGHW8yvUpPd
mSY65mXUk1odGmUMBo3/VoOW9ki9t0G6BTqK4lW4qijII
lhrVocrs6APlyAuyPbi5cCtrwQxJSd6J+h8d9t9qdZD/E
DUUdh63jdk07vmlv/+qUza15SZaAptfmFFbKOES8b7qfk
iUXvCr+kCH36lz+rTbF75cW1aU3dJ1/WWj3jgumVyqeMU
bE/OiF3ZBQA7mmz93Jho+Wis5mG07QjI3f18d+ZG0xonf
wg+sjQf3fIujCPq99PcKlM= georgechen1827@gmail.
com
~
~
~
~
~
id_rsa.pub                1,1            All
```
复制从ssh到.com的内容，粘贴到你的github->settings->SSH and GPG keys->New SSH key->Key中(Title随便取个名就行),Add SSH key即可  
然后回到终端，退出vim并且测试一下是否可以通过git连上github
```bash
# 关于退出vim，只要输入':q'回车就行
$ ssh -T git@github.com    # 测试是否能够连上github，第一次可能需要连接确认
```
顺便说一句，这个终端中所有的目录和文件都是termux应用的内部数据，从外部(如安卓手机上的文件管理器)一般是访问不到的(比如这个id_rsa.pub就无法从外部来访问)，如果你所操作的文件是在外部存储中；或者想将文件保存在外部存储中，需要给予termux访问存储设备的权限，具体操作下一节会讲到。  

* 安装nodejs

```bash
$ pkg install nodejs-lts
# 如果这里 pkg install nodejs 可能会出现npm与nodejs版本不兼容问题，具体原因未知
# 如果termux没有安装npm，需要pkg install npm
# 通过node -v和npm -v可以查看相应的版本
```

* 安装hexo

```bash
$ npm install hexo-cli -g
```

* git自己的博客源文件

先cd到你想存放博客的某个文件夹下(如果可以的话，我建议将这个文件夹设在一个能被其他应用访问到的地方，具体操作见下一节)
```bash
$ git clone git@github.com:yourname/yourname.github.io.git
# clone你的博客源文件
```

* 生成部署编写...

```bash
$ cd yourname.github.io
$ npm install
$ npm install hexo-deployer-git --save
$ hexo g
$ hexo d
```
然后就可以开始写博客啦！

### 关于termux访问外部存储

上面讲过，termux终端中所有的目录和文件都是作为应用的内部数据存在的，从外部一般访问不到(当然理论上是能访问到的，只是我水平有限)，如果你将博客源文件放在了home目录中，那就意味着你只能用termux中的vim编辑器写博文了，这既不方便也不优雅。  

在此，我的建议是，将你的博客文件存到外部存储(一个容易被你手机/平板的文件管理器访问到的)中，然后做一个文件夹的软链接到你的home目录下，这样即能够使用你手机/平板上其他的app来编辑博文，又方便你在终端中用命令同步文件(软链接可以省去输入难以记住的路径信息)。  

具体操作如下:  
* 开放存储访问权限

```bash
$ apt install termux-tools # 这是termux自带的管理工具
$ termux-setup-storage # 设置存储访问权限
# 这个时候手机应该会跳出一个权限确认弹窗，点击确定
```

* 链接一个合适的文件夹到home目录下  

开放存储访问权限之后，你可以在home目录下发现一个新目录storage，如下:  

```bash
# home目录下
$ dir
storage
$ cd storage # storage目录里面是一些常用文件夹
$ dir
dcim       movies  pictures
downloads  music   shared
$ cd shared # shared文件夹里面就是你安卓设备能访问到的根目录(不严谨地说)
$ dir
ANRSnap        Alarms         
Android        BaiduMapAuto   
DCIM           Documents      
Download       Fonts          
Foxit          GDTDOWNLOAD    
Huawei         HuaweiSystem   
Movies         Music          
Notifications  Pictures       
```

我个人是这样做的:

```bash
# shared目录下
$ mkdir github # 创建一个github文件夹，以后里面也可以clone其他项目
$ cd ˜ # 回到home目录
$ ln -s ˜/storage/shared/github github # 将刚刚创建的文件夹链接到home目录下，方便以后访问
$ cd github
$ git clone git@github.com:yourname/yourname.github.io.git # 做clone，具体不细讲，上一节有
$ cd ..
$ ln -s ˜/github/yourname.github.io hexo # 链接博客目录
$ ln -s ˜/hexo/source/_posts # 链接博客文章
# 这样，你的home目录下面应该有博客文章、github、博客三个快速访问链接
$ ls
blog  github  hexo  storage
```

---
到此所有的操作就结束了，如果各位发现我有写得不妥之处，欢迎指正！