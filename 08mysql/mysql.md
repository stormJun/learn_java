## 什么是SQL

Structured Query Language 结构化查询语言

## SQL分类
1.DDL(Data Definition Language)数据定义语言
操作数据库，表，列等
2.DML(Data Manipulation Language)数据操作语言
增删改表中的数据
3.DQL(Data Query Language)数据查询语言
用来查询表的记录(数据)。关键字：select, where 等
4.DCL(Data Control Language)数据控制语言(了解)
用来定义数据库的访问权限和安全级别，及创建用户。关键字：GRANT， REVOKE 等



## 一，DDL
### 操作数据库
### 查询
查询所有数据库的名称:
```java
SHOW DATABASES
```
### 创建
 创建数据库

```java
CREATE DATABASE db1;
```
### 修改
修改数据库的字符集

```java
ALTER DATABASE db4 CHARACTER SET utf8;
```
可以通过如下代码来进行查询数据库字符集是什么？

```java
SHOW CREATE DATABASE db4;
```
### 删除
删除数据库db4，如果存在

```java
DROP DATABASE IF EXISTS db4;
```


### 操作表
### 1.创建

```java
create table 表名(
		列名1 数据类型1,
		列名2 数据类型2,
		....
		列名n 数据类型n
	);
* 注意：最后一列，不需要加逗号（,）
```

```java
CREATE TABLE student(
					id INT,
					NAME VARCHAR(32),
					age INT ,
					score DOUBLE(4,1),
					birthday DATE,
					insert_time TIMESTAMP
				);
```
#### 复制表：

			 create table 表名 like 被复制的表名;

### 2.查询
```java
SHOW TABLES;
```
### 3.D(Delete):删除

```java
drop table 表名;
drop table  if exists 表名 ;
```
### U(Update):修改

```java
1. 修改表名
	alter table 表名 rename to 新的表名;
2. 修改表的字符集
	alter table 表名 character set 字符集名称;
3. 添加一列
	alter table 表名 add 列名 数据类型;
4. 修改列名称 类型
	alter table 表名 change 列名 新列别 新数据类型;
	alter table 表名 modify 列名 新数据类型;
5. 删除列
	alter table 表名 drop 列名;
```

## 二，DML：增删改表中数据
### 1. 添加数据：

```java
insert into 表名(列名1,列名2,...列名n) values(值1,值2,...值n);
```
**注意：**
1. 列名和值要一一对应。
2.  如果表名后，不定义列名，则默认给所有列添加值
	

```java
insert into 表名 values(值1,值2,...值n);
```
3. 除了数字类型，其他类型需要使用引号(**单双都可以**)引起来

### 2. 删除数据：

```java
delete from 表名 [where 条件]
```

1.如果不加条件，则删除表中所有记录。
2. 如果要删除所有记录
-  delete from 表名; -- 不推荐使用。有多少条记录就会执行多少次删除操作
- TRUNCATE TABLE 表名; -- **推荐使用**，效率更高 先删除表，然后再创建一张一样的表。

### 	3. 修改数据：

```java
update 表名 set 列名1 = 值1, 列名2 = 值2,... [where 条件];
```
如果不加任何条件，则会将表中所有记录全部修改。

## 三，DQL：查询表中的记录

```java
 select * from 表名;
```

```java
		select
			字段列表
		from
			表名列表
		where
			条件列表
		group by
			分组字段
		having
			分组之后的条件
		order by
			排序
		limit
			分页限定
```
### 基础查询
 **多个字段的查询**

```java
select 字段名1，字段名2... from 表名；
```

#### 去除重复：

```java
DISTINCT 
```

```java
SELECT DISTINCT address FROM student3;
```


#### 计算

```java
CREATE TABLE student3 (
id int, -- 编号
name varchar(20), -- 姓名
age int, -- 年龄
sex varchar(5), -- 性别
address varchar(100), -- 地址
math int, -- 数学
english int -- 英语
);
INSERT INTO student3(id,NAME,age,sex,address,math,english) VALUES (1,'马云',55,'男','
杭州',66,78),(2,'马化腾',45,'女','深圳',98,87),(3,'马景涛',55,'男','香港',56,77),(4,'柳岩
',20,'女','湖南',76,65),(5,'柳青',20,'男','湖南',86,NULL),(6,'刘德华',57,'男','香港
',99,99),(7,'马德',22,'女','香港',99,99),(8,'德玛西亚',18,'男','南京',56,65);
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20191113021920566.png)

```java
SELECT NAME,math,english,math+english FROM student3;
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191113021958187.png)
会有空的值，需要加上判断

```java
SELECT NAME,math,english,math+IFNULL(english,0) FROM student3;
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191113022027614.png)

#### 起别名

```java
SELECT NAME,math 数学,english 英语,math+IFNULL(english,0) 总分 FROM student3;
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20191113022313260.png)


### 条件查询
 where子句后跟条件
运算符：

```java
			* > 、< 、<= 、>= 、= 、<>
			* BETWEEN...AND  
			* IN( 集合) 
			* LIKE：模糊查询
				* 占位符：
					* _:单个任意字符
					* %：多个任意字符
			* IS NULL  
			* and  或 &&
			* or  或 || 
			* not  或 !
```
查询年龄大于20岁
```java
SELECT * FROM student3 WHERE age>20;
```
查询年龄大于等于20 小于等于30

```java
SELECT * FROM student WHERE age >= 20 AND  age <=30;
SELECT * FROM student WHERE age BETWEEN 20 AND 30;
```

查询年龄22岁，18岁，25岁的信息
```java
SELECT * FROM student WHERE age = 22 OR age = 18 OR age = 25
SELECT * FROM student WHERE age IN (22,18,25);
```
查询英语成绩为null
```java
SELECT * FROM student WHERE english IS NULL;
```
查询姓马的有哪些？ like
```java
SELECT * FROM student WHERE NAME LIKE '马%';
```



## DQL:查询语句

### 排序查询
语法：order by 子句
			* order by 排序字段1 排序方式1 ，  排序字段2 排序方式2...
			
#### 排序方式：
			 ASC：升序，默认的。
			 DESC：降序。
**注意：**
			 如果有多个排序条件，则当前边的条件值一样时，才会判断第二条件。


**查询数学成绩升序**
```java
SELECT * FROM student3 ORDER BY math ASC;
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191113023624349.png)**按照数学成绩排名，如果数学成绩一样，则按照英语成绩排名**

 如果有多个排序条件，则当前边的条件值一样时，才会判断第二条件。

```java
SELECT * FROM student3 ORDER BY math ASC ,english ASC;
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20191113024229839.png)

### 聚合函数：将一列数据作为一个整体，进行纵向的计算。

	1. count：计算个数
		1. 一般选择非空的列：主键
		2. count(*)
	2. max：计算最大值
	3. min：计算最小值
	4. sum：计算和
	5. avg：计算平均值


```java
SELECT COUNT(id) AS 总人数 FROM student;
```

**注意：聚合函数的计算，排除null值。**
解决方案：
1. 选择不包含非空的列进行计算， 一般选择非空的列：主键
2.  IFNULL函数

### 分组查询:

语法：group by 分组字段；

...