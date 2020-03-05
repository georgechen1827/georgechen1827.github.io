---
title: python spider
categories: notes
tags: [python,learning]
date: 2020-03-04 08:48:22
---

烂尾中...

---

资料主要来源于北理工的[爬虫课程](https://www.icourse163.org/learn/BIT-1001870001?tid=1206951268#)  
有requests库、beautifulsoup库、scrapy框架等

## request库

`import requests`

### request.

```python
.request()
.get() 获取网页
.head() 获取网页头
.post() 提交post请求
.put() 提交put请求
.patch() 提交局部修改请求
.delete() 提交删除请求
```

<!--more-->

### 关于url

```
url:http://host[:port][path]
http协议资源操作：
GET 请求获取url位置的资源
HEAD 获取url资源头部信息
POST 请求向资源后附加的新数据
PUT 请求向url位置存储资源，覆盖原有url位置资源
PATCH 请求向资源进行局部更新
DELETE 请求删除资源
```


### request.get(url)

```python
r=requests.get('http://www.baidu.com',) #Response

r.status_code->200/404
r.text->string text
r.encodonig->header enconding
r.apparent_encoding->text encoding
r.content->binary text
r.headers

r.raise_for_status(

requests.ConnectionError
        HTTPError
        URLRequired
        TooManyRedirects
        ConnectTimeout
        TImeout
```

#### 请求头部r.head

```python
print(r.headers)
'''
{'Cache-Control': 'private
, no-cache, no-store, proxy-revalidate, no-transform', 
'Connection': 'keep-alive', 'Content-Encoding': 'gzip', 
'Content-Type': 'text/html', 'Date': 'Sat, 11 Jan 2020 08:39:34 GMT', 
'Last-Modified': 'Mon, 23 Jan 2017 13:27:36 GMT', 'Pragma': 'no-cache', 
'Server': 'bfe/1.0.8.18', 'Set-Cookie': 'BDORZ=27315; max-age=86400; domain=.baidu.com; path=/', 
'Transfer-Encoding': 'chunked'}
'''
```

#### 在url中附加数据

```python
payload = {'key1':'value1', 'key2':'value2'}
r = requests.post('http://httpbin.org/post',data=payload)
print(r.text)
'''
{ ...
  "form": {
    "key1": "value1", 
    "key2": "value2"
  }, 
  ...
}
'''
r = requests.post('http://httpbin.org/post',data='ABC')
print(r.text)
'''
{ ...
  "data": "ABC", 
  "form": {}, 
  ...
}
'''
# r = requests.post('http://httpbin.org/post',data=payload)
```

## beautifulsoup库

```python
from bs4 import BeautifulSoup
import requests
import re
```

### 整理网页格式

```python
r = requests.get("http://python123.io/ws/demo.html")
demo = r.text   # print(demo)

soup = BeautifulSoup(demo , "html.parser") # demo->open("path.html")
print(soup.prettify)
```

### bf类的基本元素

* tag: <>...</> 标签,基本信息组织单元
* Name:<tag>.name   标签名字
* Attributs:<tag>.attrs 标签属性
* NavigableString:<tag>.string  标签内字符串
* Comment:特殊注释:<!content>为注释   

![tag](tag0.png) 

### HTML结构
HTML基本结构:树形结构

![tag](tag1.png) 

节点查找与遍历:
```pyghon
print(soup.title)
print(soup.a) #返回第一个a标签
print(soup.a.parent.name)
print(soup.a.attrs)
print(soup.a.string)

'''
<tag>.contents  儿子节点列表
<tag>.children  儿子节点迭代器
<tag>.descendent    子孙节点列表

<tag>.parent 父亲节点
<tag>.parents 父辈节点迭代器

<tag>.next_sibling(s) 同一父节点下才构成兄弟关系
<tag>.previous_sibling(s)
'''
```

```python
print(soup.find_all('a'))
print(soup.find_all(re.compile('b'))) # 返回以b开头的标签
'''
<>.find_all(name,attrs,recursive,string,**kwargs)
            名字  属性  是否搜索子孙 字符串检索
tag.find_all(True)->所有标签
tag.find_all(id='link')->attrs

soup()=soup.find_all
<tag>()=<tag>.find_all()

.fing()
.find_parents()
......

'''
```

## scrapy框架

cmd命令
```cmd
pip install scapy
scapy startproject <name> [dir] //创建工程
scrapy genspider [options] <name> <domain>  //创建爬虫
scrapy crawl <spider>
```

太乱了,写不下去了...

关于scrapy,可以参考<https://www.jianshu.com/p/cecb29c04cd2>

---
等我哪天有兴趣了再回来整理整理这篇博文

