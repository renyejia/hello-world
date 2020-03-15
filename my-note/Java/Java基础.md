# Java语言认识总结

[TOC]

## 1. Java运行环境类别

+ Java SE (Java Standard Edition)标准版：支持面向桌面级的应用

+ Java EE(Java Enterprise Edition)企业版：主要针对于Web应用程序的开发

+ JRE

## 2. Java特点

+ 简单性、面向对象、分布式、健壮性、安全性、体系结构中立、可移植性、解释型、高性能、多线程、动态性。

### 面向对象

Java 与 C++ 不同之处在于多重继承，在Java中，取而代之的是接口的概念。

### 可移植性

与C和C++不同，Java中的基本数据类型的大小以及有关运算都做了明确的说明。
例如，Java中 int 永远为32位的整数，而C/C++ 中，int 可能是16位整数、32位整数，也可能是编译器提供商指定的其他大小，唯一的限制只是 int 类型的大小不能低于 short int, 并且不能高于 long int。

## 3. 安装设置JDK

+ 在Windows上，启动安装程序，会询问安装位置，默认为`C:\Program Files\Java\jdk1.8.0_version`(版本可能不同)

+ 在Mac上，运行安装程序，会把软件安装到`/Libraiy/Java/JavaVirtualMachines/jdk1.8.0_version.jdk/Contents/Home`

+ 在 Linux上，只需要把 `.tar.gz` 文件解压缩到你选择的某个位置，如你的主目录，或者
`/opt`。如果从 `RPM` 文件安装，则要反复检查是否安装在 `/usr/java/jdkl.8.O_version`。

### 在Windows上配置运行环境

右键点击我的电脑，打开 → 属性 → 高级系统设置 → 环境变量 → 系统变量：

+ 新建一个系统变量：
  + 变量名：JAVA_HOME</br>
  + 变量值：D:\PATH\Java\jdk-13.0.1`(Java安装路径)`</br>
+ Path变量 → 添加变量值：***( 用一个分号分隔新增 )***
  + %JAVA_HOME%\bin
  + %JAVA_HOME%\jre\bin

配置完成后，按键盘 `win + R` 输入 `cmd`，在命令提示框内输入`java -version`，看到安装的jdk版本，即环境配置成功。
