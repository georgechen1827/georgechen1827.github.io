---
title: Lucence相关
categories: notes
tags: [搜索引擎,c#,learning]
date: 2020-02-24 18:01:26
---

未完结,不定期更新

---

参考:  
<https://www.cnblogs.com/forfuture1978/archive/2010/06/13/1757479.html>  
<http://lucene.apache.org/>  
<https://blog.csdn.net/PZ_eng/article/details/91977083>

## 总论

### 全文检索

#### 生活中数据总体分为如下几种:  
* 结构化数据: 具有固定格式或有限长度的数据(数据库,元数据)
* 非结构化数据: 不定长或无固定格式数据(word文档)
* 半结构化数据: 可根据需要当成结构化数据处理,也可以抽取纯文本按非结构化数据处理  

其中,非结构化数据又叫全文数据

#### 全文数据搜索主要有两种方法:
* 顺序扫描法: 直接,方便,较慢
* 索引法: 将非结构化数据中一部分信息提取出来重新组织,使其有一定结构后再搜索  
 
索引构成了全文检索的基本思路  
这种先建立索引,再对索引进行搜索的过程就叫做全文检索

全文检索大体分为两个过程: 索引创建,搜索索引

#### 因此,全文检索需要关注下面三个问题:
1. 索引里面应该存什么(index)
2. 如何创建索引(indexing)
3. 如何对索引进行搜索(search)

### 索引里面应该存什么--倒排索引

倒排索引一般形式如下:
> token1->doc1 doc2 doc3 ...  
> token2->doc3 doc5 doc6 ...

其中:
* token所在的地方称为词典
* 每个token指向一个文档链表,此链表称为倒排表

通过这种索引方式,加上对链表的一系列操作,可以大大加速全文搜索的速度

### 索引创建一般过程

创建索引一般分为如下几步:
1. 整理要索引的Document
2. 将Document传给Tokenizer,得到Token(分词)
3. 将Token传给Linguistic Processor进行预处理,得到Term(转变大小写,词性,单复数)
4. 将Term传给Indexer进行倒排索引

### 搜索一般过程

对索引进行搜索一般分为如下几步:
1. 用户输入query
2. 对query进行词法,语法分析以及语言处理,得到语法树
3. 搜索索引,得到符合语法树的文档
4. 根据得到的文档和query的相关性对结果进行排序

### Lucence

Lucence是一个由Java实现的,支持纯文本文件的索引和搜索的高效、可扩展的全文检索框架

#### Lucence和外界的交互如下所示:  
![Lucence](Lucence0.png)

#### Lucence内部结构如下:  
![Lucence](Lucence1.png)

其中:
* 被索引的文档用Document对象表示  
* IndexWriter通过函数addDocument将文档添加到索引中 ,实现创建索引的过程  
* Lucene的索引是应用倒排索引  
* 当用户有请求时,Query代表用户的查询语句  
* IndexSearcher通过函数search搜索Lucene Index  
* IndexSearcher计算term weight和score并且将结果返回给用户
* 返回给用户的文档集合用TopDocsCollector表示  

#### Lucence索引过程如下:
1. 创建一个IndexWriter用来写索引文件,它有几个参数,INDEX_DIR 就是索引文件所存放的位置,Analyzer便是用来对文档进行词法分析和语言处理的 
2. 创建一个 Document 代表我们要索引的文档 
3. 将不同的Field加入到文档中;我们知道,一篇文档有多种信息,如题目,作者,修改时间,内容等;不同类型的信息用不同的Field来表示  
4. IndexWriter调用函数addDocument将索引写到索引文件夹中 　

#### Lucence搜索过程如下:
1. IndexReader将磁盘上的索引信息读入到内存
2. 创建IndexSearcher准备进行搜索  
3. 创建Analyer用来对查询语句进行词法分析和语言处理 
4. 创建QueryParser用来对查询语句进行语法分析 
5. QueryParser调用parser进行语法分析,形成查询语法树,放到Query中  
6. IndexSearcher调用search对查询语法树Query进行搜索,得到结果TopScoreDocCollector

#### Lucence的包结构可由如下图表示:
![Lucence](Lucence2.png)

其中:
* Lucene的analysis模块主要负责词法分析及语言处理而形成Term  
* Lucene的index模块主要负责索引的创建,里面有里面有IndexWriter
* Lucene的store模块主要负责索引的读写
* Lucene的QueryParser主要负责语法分析
* Lucene的search模块主要负责对索引的搜索
* Lucene的similarity模块主要负责对相关性打分的实现  

## C#中的Lucence

<http://lucenenet.apache.org/>











