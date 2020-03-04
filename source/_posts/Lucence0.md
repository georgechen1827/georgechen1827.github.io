---
title: Lucence相关
categories: notes
tags: [搜索引擎,c#,learning]
date: 2020-02-24 18:01:26
---

~~未完结,不定期更新~~  完结

---

Lucence是一个由Java实现的,支持纯文本文件索引和搜索的高效、可扩展、开源的的全文检索框架

因自己需要用到lucence.net相关知识, 学习时参阅了不少资料, 将一些要点记录在此, 以供参考

## 总论

参考:  
<https://www.cnblogs.com/forfuture1978/archive/2010/06/13/1757479.html>  
<https://blog.csdn.net/PZ_eng/article/details/91977083>  
 
<http://lucene.apache.org/>  

### 全文检索

#### 数据的分类  
生活中数据总体分为如下几种:
* 结构化数据: 具有固定格式或有限长度的数据(数据库,元数据)
* 非结构化数据: 不定长或无固定格式数据(word文档)
* 半结构化数据: 可根据需要当成结构化数据处理,也可以抽取纯文本按非结构化数据处理  

其中,非结构化数据又叫全文数据

#### 全文数据搜索的主要方法
* 顺序扫描法: 直接,方便,较慢
* 索引法: 将非结构化数据中一部分信息提取出来重新组织,使其有一定结构后再搜索  
 
索引构成了全文检索的基本思路  
这种先建立索引,再对索引进行搜索的过程就叫做全文检索

全文检索大体分为两个过程: 索引创建,搜索索引

#### 全文检索需要关注的问题
因此,全文检索需要关注下面三个问题:  
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

#### Lucence和外界的交互  
![Lucence](Lucence0.png)

#### Lucence内部结构  
![Lucence](Lucence1.png)

其中:
* 被索引的文档用Document对象表示  
* IndexWriter通过函数addDocument将文档添加到索引中 ,实现创建索引的过程  
* Lucene的索引是应用倒排索引  
* 当用户有请求时,Query代表用户的查询语句  
* IndexSearcher通过函数search搜索Lucene Index  
* IndexSearcher计算term weight和score并且将结果返回给用户
* 返回给用户的文档集合用TopDocsCollector表示  

#### Lucence索引过程
1. 创建一个IndexWriter用来写索引文件,它有几个参数,INDEX_DIR 就是索引文件所存放的位置,Analyzer便是用来对文档进行词法分析和语言处理的 
2. 创建一个 Document 代表我们要索引的文档 
3. 将不同的Field加入到文档中;我们知道,一篇文档有多种信息,如题目,作者,修改时间,内容等;不同类型的信息用不同的Field来表示  
4. IndexWriter调用函数addDocument将索引写到索引文件夹中 　

#### Lucence搜索过程
1. IndexReader将磁盘上的索引信息读入到内存
2. 创建IndexSearcher准备进行搜索  
3. 创建Analyer用来对查询语句进行词法分析和语言处理 
4. 创建QueryParser用来对查询语句进行语法分析 
5. QueryParser调用parser进行语法分析,形成查询语法树,放到Query中  
6. IndexSearcher调用search对查询语法树Query进行搜索,得到结果TopScoreDocCollector

#### Lucence的包结构
![Lucence](Lucence2.png)

其中:
* Lucene的analysis模块主要负责词法分析及语言处理而形成Term  
* Lucene的index模块主要负责索引的创建,里面有里面有IndexWriter
* Lucene的store模块主要负责索引的读写
* Lucene的QueryParser主要负责语法分析
* Lucene的search模块主要负责对索引的搜索
* Lucene的similarity模块主要负责对相关性打分的实现  

## Lucence.net

参考:  
<http://lucenenet.apache.org/>  
<https://www.cnblogs.com/xiaoyaodijun/p/4140507.html>  
<https://blog.csdn.net/xuezhongsong/article/details/4388241>

### lucence.net中主要的几个类

#### Document

Document用于描述一个文档,由多个Field(相当于属性)组成

常用方法: 
```C#
public sealed class Document{
    public Document();
    puclib void Add(IFieldable field);  //  添加字段/属性field
    public Field GetField(string name); //  获得第一个名为name的field,无则返回null
    public string Get(string name); // 获得第一个名为name的field 中的文本内容
    public Field[] GetFields(string name);  //获得所有名为name的field,无则返回null
    public string[] GetValues(string name); //  获得所有名为name的field 中的文本内容
}
```

#### Field

Field用于描述一个文档的某个属性,一般由名字和属性值构成

常用方法:
```C#
public sealed class Field : AbstractField, IFieldable{
    //  inherited
    public virtual string Name { get; } //  名字
    public override string StringValue { get; } //  属性值
    
    public Field(string name, string value, Store store, Index index);
    public void SetValue(string value); //更改属性值   
}
```

关于构造函数中的参数的说明:
* name: 字段名称
* value: 字段内容,也就是属性值
* store: 存储类型
> Field.Store有三个属性：  
>* Field.Store.YES: 索引文件本来只存储索引数据,此设计将原文内容直接也存储在索引文件中,如文档的标题
>* Field.Store.NO：原文不存储在索引文件中，搜索结果命中后，再根据其他附加属性如文件的Path，数据库的主键等，重新连接打开原文，适合原文内容较大的情况。
>* Field.Store.COMPRESS 压缩存储  
         
* index: 索引类型
> Field.Index有四个属性：
>* Field.Index.TOKENIZED：分词索引
>* Field.Index.UN_TOKENIZED：进行索引，但不对其进行分词，如作者名，日期等，Rod Johnson本身为一单词，不再需要分词。
>* Field.Index.NO 和 Field.Index.NO_NORMS: 不进行索引，存放不能被搜索的内容如文档的一些附加属性如文档类型, URL等  

#### Analyzer

在一个文档被索引之前，首先需要对文档内容进行分词处理，这部分工作就是由 Analyzer 来做的。Analyzer 类是一个抽象类，它有多个实现。针对不同的语言和应用需要选择适合的 Analyzer。Analyzer 把分词后的内容交给 IndexWriter 来建立索引。

一般用法(不太会用,先这么写着吧):
```C#
StandardAnalyzer analyzer = new StandardAnalyzer(Version.LUCENE_CURRENT);
```

#### IndexWriter

IndexWriter 是 Lucene 用来创建索引的一个核心的类，他的作用是把一个个的 Document 对象加到索引中来。建立索引必须从它开始。而且，从它的构造函数开始

一般用法:
```C#
 IndexWriter writer = new IndexWriter(string idxDir,Analyzer analyzer,bool isNewCreate,MaxFieldLength IndexWriter.MaxFieldLength.LIMITED);
 
 writer.AddDocument(doc);//向索引文件中写数据 
writer.Optimize();// 索引优化，一般执行此步骤时，所消耗的内存是写入索引所需内存的2倍，在执行索引生成操作的时候本身就对内存有比较大的消耗，最好在索引创建完成之后，执行此步骤。 
writer.Commit();//数据提交 
writer.Rollback();//数据回滚 
writer.Close();//关闭流索引写入器，此步骤才真正将数据写入到索引文件中。 
```

#### Directory

这个类代表了 Lucene 的索引的存储的位置，这是一个抽象类，它目前有两个实现，第一个是 FSDirectory，它表示一个存储在文件系统中的索引的位置。第二个是 RAMDirectory，它表示一个存储在内存当中的索引的位置

一般用法:
```C#
string indexDir = "idx";
DirectoryInfo dir = new DirectoryInfo(indexDir);

Lucene.Net.Store.Directory idxDir = new SimpleFSDirectory(dir, new SimpleFSLockFactory());  //  创建上面的indexwriter需要用到
```

### Lucence.net中的索引建立

总结一下建立索引的一般过程
```C#
/*  前期准备    */
var indexDir = "idx";   //  索引目录
var isNewCreate = true;

DirectoryInfo dir = new DirectoryInfo(indexDir);
Lucene.Net.Store.Directory idxDir = new SimpleFSDirectory(dir, new SimpleFSLockFactory());

StandardAnalyzer analyzer = new StandardAnalyzer(Version.LUCENE_CURRENT);

IndexWriter writer = new IndexWriter(idxDir, analyzer, isNewCreate, IndexWriter.MaxFieldLength.LIMITED);
// writer.MergeFactor(50); 多少个合并一次【优化缓存】 
// writer.MaxMergeDocs(5000); 一个segment最多有多少个document【优化索引存储的segment文件】 


/*  写索引   */
Document doc = new Document();
Field field = new Field("name", "content", Field.Store.YES, Field.Index.ANALYZED);
doc.Add(field);
writer.AddDocument(doc);


/*  关文件   */
writer.Optimize();
writer.Commit(); 
writer.Rollback(); 
writer.Close(); 
```

### Lucence.net中的索引搜索

下面是我自己写的一个索引搜索的流程模板
```C#
var indexDir = "idx";   //  指定索引的目录
IndexSearcher searcher = new IndexSearcher(LuceneConnection.GetIndexDirectory(indexDir));// 建立搜索引擎; readOnly 为boolean值

StandardAnalyzer analyzer = new StandardAnalyzer(Version.LUCENE_CURRENT);   //  分词器用于分析query,此分词器应当与建立索引的分词器保持一致

// MultiFieldQueryParser parser = new MultiFieldQueryParser(Version.LUCENE_CURRENT, new string[] { title, content }, analyzer); 多字段搜索   
var q = new QueryParser(Version.LUCENE_CURRENT, "name", new StandardAnalyzer(Version.LUCENE_CURRENT)).Parse("content");   //  单字段搜索,字段是name搜索词是content   

SortField sfield = new SortField(null, SortField.SCORE, true);
Sort sort = new Sort(sfield);    //  指定一个排序方式

var hits = searcher.Search(q, null, searcher.MaxDoc, sort); //  搜索,返回前searcher.MaxDoc个Docs组成的TopFieldDocs
//TopFieldDocs docs = searcher.Search(q,null, searcher.MaxDoc, sort);


/*  下面是通过搜索结果获取Doc的一般方法  */
ScoreDoc[] scoreDocs = hits.ScoreDocs;//权值对象 包含document下标信息，能确定searcher中的document的下标。 
int docCount = scoreDocs.Length;// 结果个数统计  
Document doc = searcher.Doc(scoreDocs[docCount - 1].Doc); // 通过document下标值，获取document对象 

//  输出结果
Console.WriteLine("字段{2}搜索到:{0} 字段{3}搜索到:{1}", doc.Get("name"), doc.Get("content"), "name", "hello");
searcher.Close();

```

---
说实话,本人没有对搜索引擎有过系统的学习,文中有些地方也是根据自己的理解来写的; 如果各位发现有写得不妥之处，欢迎指正！







