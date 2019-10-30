## 基本组成：

Java语言基础由关键字、 标识符、 注释、 常量和变量、 运算符、 语句、 函数和数组等组成。 

### 关键字：
- volatile
- transient:关键字标记的成员变量不参与序列化过程

### 标识符
#### Java中的名称规范

> 1.包名： 多单词组成时所有字母都小写。
> 例如： xxxyyyzzz
> 2.类名接口名： 多单词组成时， 所有单词的首字母大写。
> 例如： XxxYyyZzz
> 3.变量名和函数名： 多单词组成时， 第一个单词首字母小写， 第二个单词开始每个单词首字母大写。
> 例如： xxxYyyZzz
> 4.常量名： 所有字母都大写。 多单词时每个单词用下划线连接。
> 例如： XXX_YYY_ZZZ 
>

### Java语言的数据类型

位（bit）于字节（byte）的关系：

1Byte = 8bit

1个字节8位。

| 数据类型 | 字节数 |
| -------- | ------ |
| byte     | 1      |
| short    | 2      |
| int      | 4      |
| long     | 8      |
| float    | 4      |
| double   | 8      |
| char     | 1      |



![1570706220(1)](https://img-blog.csdnimg.cn/20191010191826799.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3N4ajE1OTc1Mw==,size_16,color_FFFFFF,t_70)



long类型后面加l

```
long l = 123456789123l
```



### 类型转换

- 自动类型转换 

```
int x = 3;
byte b = 5;
x = x + b;
```

输出8

- 强制转换
```
byte b = 3;
b = (byte)(b+200)
```
注意：

1.只有数值类型才能进行加法操作， 非数值类型不行。

```
true+1
```

会报错

2.**char类型数据也可以和int类型相加**， 但是首先char类型数据会被自动提升为int类型 。



#### 面试题：

```
  byte b = 3+7;//不会报错 因为char类型数据也可以和int类型相加， 但是首先char类型数据会被自动提升为int类型
        byte b1 = 3;
        byte b2 = 7;
        b = b1+b2;//它根本不知道b1和b2到底是多少， 两个byte类型的数据相加时， 首先都会被提升为int类型， 他们的和也是int类型， 其值可能会超过byte的范围， 因此就会报错。
 
```

ide会有提示。


### 运算符
>1.整数与整数相除时， 结果永远是整数， 小数部分被忽略
>
>2.负数对正数取模结果为负数。正数对负数取模结果为正数。
```
5%5 0
-5%2 -1
5%-2 1
```

