可以通过map集合来进行缓存，map集合缺点：多台电脑不合适，内存小。

非关系形数据库：适合分布式。

五种数据结构：

		1) 字符串类型 string
	    2) 哈希类型 hash
	    3) 列表类型 list
	    4) 集合类型 set
	    5) 有序集合类型 sortedset





### 字符串类型 string

1. 存储： set key value

  ```
  127.0.0.1:6379> set username zhangsan
  OK
  ```

2. 获取： get key

  ```
 127.0.0.1:6379> get username
"zhangsan"
  ```
3. 删除： del key
```
127.0.0.1:6379> del age
```

