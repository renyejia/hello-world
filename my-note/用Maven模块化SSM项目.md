# ——

1. 创建一个简单的父项目，命名就项目的名字，例如 study
2. 然后建立子模块，新建 new Maven Module，命名为 项目名+dao ，例如，study-dao，parent 为 study
3. 查看一下，study-dao的pom.xml文件中有没有下面这种格式的代码：

```xml
    <parent>
        <groupId></groupId>
        <artifactId></artifactId>
        <version></version>
    </parent>
```
