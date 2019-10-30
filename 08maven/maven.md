1.依赖

2.一键构建：mvn tomact:run 可以启动项目。

3.环境变量添加：

```
 mvn –v
```

4：本地maven jar包的位置：

```
C:\maven\apache-maven-3.3.9\conf\settings.xml
```

修改这个文件位置即可，不用去中央仓库，直接从本地下载。
```
<localRepository>C://maven/localmaven</localRepository>
```

5.maven标准目录结构

```
src/main/java —— 存放项目的.java 文件
src/main/resources —— 存放项目资源文件，如 spring, hibernate 配置文件
src/test/java —— 存放所有单元测试.java 文件，如 JUnit 测试类
src/test/resources —— 测试资源文件
target —— 项目输出位置，编译后的 class 文件会输出到此目录
pom.xml——maven 项目核心配置文件
```

```
注意：如果是普通的 java 项目，那么就没有 webapp 目录。
```

6maven命令



```
mvn clean 删除本地编译的信息
```



```
 mvn compile 把src/main下的命令进行编译
```



```
mvn test 是 maven 工程的测试命令 mvn test，会执行 src/test/java 下的单元测试类
```



```
mvn package 是 maven 工程的打包命令，对于 java 工程执行 package 打成 jar 包，对于 web 工程打成 war包。
```



```
mvn package 是 maven 工程的打包命令，对于 java 工程执行 package 打成 jar 包，对于 web 工程打成 war包。
```



### 概念模型



项目自身信息

项目运行锁依赖的jar包信息

项目运行环境信息



