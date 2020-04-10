---
title: mysql使用
categories: [notes,学位课程]
tags: [数据库,learning]
date: 2020-03-27 15:18:05
---

<http://c.biancheng.net/view/2433.html>
#### 建立用户账户及更改权限
`GRANT ALL ON DataBaseA.* TO 'root'@'localhost';`

#### mysql数据存储位置
这个位置文件的路径在my.ini中datadir中可以找到  

一般情况下,my.ini在mysql安装目录下(例如C:\ProgramData\MySQL\MySQL Server 8.0)

#### 创建数据库及表

```
mysql> create database school;
Query OK, 1 row affected (0.00 sec)

mysql> use school;
Database changed

mysql> create table Student(
    -> Sno char(6),
    -> Sname varchar(8),
    -> Ssex char(2),
    -> Sage smallint,
    -> Sdept varchar(15)
    -> );
```

#### 修改数据表

```
ALTER TABLE <表名>
{ ADD COLUMN <列名> <类型>
| CHANGE COLUMN <旧列名> <新列名> <新列类型>
| ALTER COLUMN <列名> { SET DEFAULT <默认值> | DROP DEFAULT }
| MODIFY COLUMN <列名> <类型>
| DROP COLUMN <列名>
| RENAME TO <新表名> }
```
添加约束<https://blog.csdn.net/qq_36855487/article/details/82945567>