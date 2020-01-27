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

4. 然后查看一下，study的pom.xml 就是父项目的pom.xml 是否有

    ```xml
        <modules>
            <module>study-dao</module>
        </modules>
    ```

5. 和上面一样的流程建立study-service ，但同时要注意 study-service 模块需要引入 study-dao ，在study-service模块的pom.xml 文件中加上，spring-context也需要用到，加上。

    ```xml
        <dependencies>
            <dependency></dependency>
            <dependency></dependency>
        </dependencies>
    ```

6. 建立spring-web ，模块上有一点不同，这个是需要打成 war 包的，如果有报错可能是需要加入运行服务的环境，即需要配置Tomcat
