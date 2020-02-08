---
title: About the Blog
categories: instructions
tags: [instructions,hexo]
date: 2020-02-06 00:26:15
---

### 搭建参考

搭建：<https://zhuanlan.zhihu.com/p/44213627>  
主题使用：<https://github.com/Shen-Yu/hexo-theme-ayer>  
分类设置：<https://www.zhihu.com/question/29017171>

### 常用命令

``` bash
# 本地运行博客
$ hexo g
$ hexo server 

# 部署博客到github
$ hexo clean    # 可不加
$ hexo generate # hexo g
$ hexo deploy   # hexo d

# 更新hexo分支
$ git pull origin hexo  # 同步博客
$ git add .     # .github.io目录下
$ git commit -m "update hexo branch" # 带解释地提交
$ git push      # 默认分支为hexo, -f 进行强制覆盖

# 新建博文
$ hexo new [layout] <title>

# 新建菜单页
$ hexo new page <title>

# 新建草稿
$ hexo new draft <title>
$ hexo server --draft   # 预览草稿
$ hexo publish draft newpage    # 发布草稿
```

### markdown语法

<https://www.jianshu.com/p/ebe52d2d468f>  
<https://www.runoob.com/markdown/md-tutorial.html>