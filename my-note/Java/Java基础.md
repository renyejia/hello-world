# Java基础笔记

[TOC]

## 一、Java语言认识总结

### 1.1 Java运行环境类别

+ Java SE (Java Standard Edition)标准版：支持面向桌面级的应用
+ Java EE(Java Enterprise Edition)企业版：主要针对于Web应用程序的开发

### 1.2 Java 特点

+ 简单性
+ 面向对象：Java 与 C++ 不同之处在于多重继承，在Java中，取而代之的是接口的概念。
+ 分布式
+ 健壮性
+ 安全性
+ 体系结构中立
+ 可移植性：与C和C++不同，Java中的基本数据类型的大小以及有关运算都做了明确的说明。

+ + 例如，Java中 int 永远为32位的整数，而C/C++ 中，int 可能是16位整数、32位整数，也可能是编译器提供商指定的其他大小，唯一的限制只是 int 类型的大小不能低于 short int, 并且不能高于 long int。

+ 解释型
+ 高性能
+ 多线程
+ 动态性

## 二、Java程序设计环境

### 2.1 下载JDK

网址：https://www.oracle.com/java/technologies/javase-downloads.html



![image.png](https://cdn.nlark.com/yuque/0/2020/png/641808/1585635237434-00d74bb1-48a1-4c76-84a4-1d5aa50ac0f1.png)



+ 在Windows上，启动安装程序，会询问安装位置，默认为 `C:\Program Files\Java\jdk1.8.0_version` (版本可能不同)
+ 在Mac上，运行安装程序，会把软件安装到`/Libraiy/Java/JavaVirtualMachines/jdk1.8.0_version.jdk/Contents/Home`
+ 在 Linux上，只需要把 `.tar.gz` 文件解压缩到你选择的某个位置，如你的主目录，或者`/opt`。如果从 ***RPM*** 文件安装，则要反复检查是否安装在` /usr/java/jdkl.8.O_version` 。



### 2.2 在Windows上配置运行环境



右键点击 **我的电脑**，**打开** → **属性** → **高级****系统****设置** → **环境****变量** → **系统****变量**：



+ 新建一个系统变量：

+ + 变量名：JAVA_HOME
  + 变量值：D:\PATH\Java\jdk-13.0.1 *（此处填写自己的 Java安装路径）*

+ Path变量 → 添加变量值：*( 用一个分号分隔新增 )*

+ + %JAVA_HOME%\bin
  + %JAVA_HOME%\jre\bin



配置完成后，按键盘 win + R 输入 cmd，在命令提示框内输入 `java -version` ，看到安装的jdk版本，即环境配置成功。



## 三、Java基本程序结构



### 3.1 一个简单的Java应用程序



```java
public class FirstSample{
    public static void main(String[] args){
    System.out.println("Hello World");
  }
}
```



注：Java区分大小写

类名的定义规则：

必须以字母开头，后面可以跟字母或数字的任意组合。长度基本无限制。但不能使用Java保留字。

[**标准的命名规范**](https://www.yuque.com/yu-fool/ngr850/tqf8mg)：

类名是以大写字母开头的名词。若由多个单词组成，则每个单词首字母大写。即驼峰命名法。



### 3.2 注释



三种注释方法

```java
//双斜杠为常用注释方法，注释一行内容
/*当需要一段长篇的注释，注释一段内容*/
/**
 * @version 2.1.3
 * @author pc
 */
//第三种在Java的编辑器中，以/**开始，然后回车，大部分可以自动填充，以*/结束。
```

注：在Java中，注释不可以嵌套。



### 3.3 数据类型



在Java中，一共有8种基本类型（primitive type），其中有4种整型、2种浮点型、1种用于表示 Unicode编码的字符单元的字符类型 char 和 1种用于表示真值的 boolean 类型。



+ 整型



| 类型  | 存储需求 | 取值范围                                               |
| ----- | -------- | ------------------------------------------------------ |
| int   | 4字节    | -2 147 483 648 ~ 2 147 483 647 (正好超过20亿)          |
| short | 2字节    | -32 768 ~ 32 767                                       |
| long  | 8字节    | -9 223 372 036 854 775 808 ~ 9 223 372 036 854 775 807 |
| byte  | 1字节    | -128 ~ 127                                             |



> 注意， Java 没有任何无符号（unsigned ) 形式的 int、long、short 或 byte 类型。

+ 浮点类型



| 类型   | 存储需求 | 取值范围                                             |
| ------ | -------- | ---------------------------------------------------- |
| float  | 4字节    | 约 ± 3.402 823 47E+38F (有效位数为 6~7位)            |
| double | 8字节    | 约 ± 1.797 693 134 862 315 70E+308 (有效位数为 15位) |



+ char类型

+ + char类型的字面量值要用单引号括起来。例如：'A' 是编码值为 65 所对应的字符常量。

+ boolean类型

+ + (布尔）类型有两个值：false 和 true，用来判定逻辑条件，整型值和布尔值之间不能进行相互转换。



### 3.4 变量



+ **变量**

+ + 逐一声明每一个变量可以提高程序的可读性。
  + 声明一个变量之后，必须用赋值语句对变量进行显式初始化，千万不要使用未初始化的变量。

+ **常量**

+ + 在 Java中，利用关键字 final指示常量。
  + 关键字 final 表示这个变量只能被赋值一次。习惯上，常量名使用全大写。例如：

```java
final double CM_PER_INCH = 2.54;
```



+ + 可以使用关键字 static final 设置一个类常量，可以在一个类中的多个方法中使用。

```java
public class Constant2{
    public static final double CM_PER_INCH = 2.54;
    public static void main(String[] args){
        ......
    }
}
```



需要注意，类常量的定义位于 main 方法的外部。因此，在同一个类的其他方法中也可以使用这个常量。

而且，如果一个常量被声明为 public，那么其他类的方法也可以使用这个常量。



### 3.5 运算符



“%”取模，求余数。

两个整数相除，得到整数。否则，得到浮点数。

例：15/2 等于7，15%2 等于1，15.0/2 等于7.5 。

整数被 0 除会产生异常，浮点数被 0 除会得到无穷大或NaN。



#### 3.5.1 数学函数与常量



通过网址：https://www.oracle.com/java/technologies/javase-downloads.html 

点击对应的 Documentation Download，类似于 jdk-14_doc-all.zip 文件样式的API文档。

通过在API文档中搜索Math，可以了解到相关的一些数学函数。



**数值转换**

合法转换："小的"可以转化为"大的"

【 byte → short → int → long】 （无信息丢失）

【 char → int → double】、【 float → double】 （可能有精度损失）

【 int → float】、【 long → float】、【 long → double】（可能有精度损失）

大转化为小，需强制类型转换。



#### 3.5.2 关系和 boolean 运算符



+ 三元操作符：

+ + x < y ? x : y  会返回x、y中，小的那个。

&& 逻辑 (与)、  || 逻辑 (或)、  ! 逻辑 (非)



#### 3.5.3 位运算符



**& 与 ("and") 、| 或 ("or")、^ 异或 ("xor")、~ ("not")**



+ "&"与"&&"的区别：  

+ + 单&时，左边无论真假，右边都进行运算。
  + 双&时，如果左边为真，右边参与运算；如果左边为假，右边不参与运算。

+ "|"和"||"的区别同理：

+ + || 表示：当左边为真时，右边不参与运算。

+ 异或( ^ )与或( | )的不同之处：

+ + 当左右都为true时，结果为false。

+ \>>或<< 移位运算符

+ + 1<<35的值等同于 1<<3 或 8。
  + 移位运算符的右操作数要完成模32的运算；若左操作数是long类型，则右操作数要模64。



| 运算符 | 范例                                         | 说明                                                         |
| ------ | -------------------------------------------- | ------------------------------------------------------------ |
| <<     | 3<<2=12，即二进制011左移两位为1100，3*2*2=12 | 空位补0，被移除的高位丢弃，空缺位补0。                       |
| >>     | 3>>1=1，即二进制011右移一位得001，3/2=1      | 被移位的二进制最高位是0，右移后，空缺位补0；                 |
| >>>    | 3>>>1=1，无符号右移，3/2=1                   | 被移位二进制最高位无论是0或者是1，空缺位都用0补。            |
| &      | 6 & 3 = 2，二进制110 & 011=010               | 二进制位进行&运算，只有1&1时结果是1，否则是0                 |
| \|     | 6 \| 3 = 7，二进制110 \| 011 = 111           | 二进制位进行 \| 运算，只有0 \| 0时结果是0，否则是1           |
| ^      | 6 ^ 3 = 5，二进制110异或011=101              | 相同二进制位进行 ^ 运算，结果是0；1^1=0 , 0^0=0不相同二进制位 ^ 运算结果是1；1^0=1 , 0^1=1 |
| ~      | ~6=7，二进制110取反码-111                    |                                                              |



**枚举类型**

```java
enum Size {SMALL, MEDIUM, LARGE, EXTRA_LAGRE};
//然后就可以声明
Size s = Size.MEDIUM;
```



### 3.6 字符串

概念上，Java字符串就是Unicode字符序列。Java没有内置的字符串类型。每个用双引号括起来的字符串都是String类的实例。

+ 子串：String类的substring方法可以从一个较大的字符串提取出一个子串。
+ 拼接：允许使用"+"号连接字符串。

+ + 当一个字符串与一个非字符串拼接时，后者被转化成字符串。
  + 任何一个Java对象都可以转换成字符串 。例如：`System.out.println("The answer is " + answer);`



#### 3.6.1 不可变字符串 ==String==



+ String没有用于修改字符串的方法。
+ 优点：编译器可以让字符串共享。

+ + 想象成字符串存放在公共的存储池中。字符串变量指向存储池中的相应位置。复制字符串变量即为共享字符；

+ 将字符串变量重新赋值，原始字符串放置在堆中，Java将自动地进行垃圾回收；如果一块内存不再使用了，系统最终会将其回收。



#### 3.6.2 检测字符串是否相等



+ ==equals方法==，`s.equals(t)`若相等，则返回true。

`"Hello".equals(greeting)`这个是合法的。即可以是字符串变量也可以是字符串字面量。

+ 检测两字符串是否相等，不区分大小写，可以用 `equalsIgnoreCase`方法。
+ “==”只能检测两个字符串是否放在同一个位置，不能检测字符串内容相等。当然，两字符串位置相等内容必然一样，但是可能出现内容相同的字符串放在不同位置的情况。



如果虚拟机始终使用相同的子符串共享，就可以使用 == 运算符检测是否相等。但实际上只有字符串常量是共享的，而 "+"或"substring"等操作产生的结果并不是共享的。



+ 空串与NULL串

+ + 空串""是长度为0内容为空的字符串。`if(str.length == 0)` 或 `if(str.equals(""))`可以检查是否为空。
  + null 表示目前没有任何对象与该变量关联。`if(str == null)`
  + `if( str != null && str.length != 0)` 首先检查 str 不为 null 。如果在一个null值上调用方法，会出现错误。



+ StringAPI ：有许多方法，需要的时候可以查看 [JavaAPI文档](https://www.oracle.com/java/technologies/javase-downloads.html) (👈网址链接是Oracle官网下载Documentation的地方)。



#### 3.6.3 构建字符串(String/StringBuilder/StringBuffer)

+ + 有时候，需要由多个较短的字符串构建字符串。采用字符串连接的方式效率低，每次连接字符串都会构建一个新的String对象，耗时又浪费空间。使用StringBuilder类可以避免这个问题。

```java
StringBuilder builder = new StringBuilder();
builder.append(ch);//添加一个char字符
builder.append(str);//添加一个字符串
String completedString = builder.toString();
```



+ + StringBuffer ：允许使用多线程的方式执行添加或删除字符的操作。若是所有字符串在一个单线程中编辑，用StringBuilder替代它。



### 3.7 输入输出



#### 3.7.1 读取输入

+ “标准输出流”（即控制台窗口）：System.out.println
+ “标准输入流”System.in ：

+ + 首先构造一个 Scanner 对象，并与 System.in 关联 `Scanner in = new Scanner(System.in);`
  + 然后可以使用Scanner类的各种方法实现输入。例：`String name = in.nextLine();`



Console可以在控制台不可见的读取密码。

```java
Console cons = System.Console();
String username = cons.readLine("User name:");
char[] passwd = cons.readPassword("Password:");
```

安全起见存放在一维字符数组中。



#### 3.7.2 格式化输出

`System.out.printf("%8.2f",x);`用 8个字符的宽度和小数点后两个字符的精度打印 x 。

用于 printf 的转换符

![image.png](https://cdn.nlark.com/yuque/0/2020/png/641808/1585643742650-74a923a4-30d2-4b7c-b6ae-bee732b9072c.png)df



#### 3.7.3 文件输入与输出



**读取文件**

```java
Scanner in = new Scanner(Paths.get("myfile.txt"),"UTF-8");
```

💡这里指定了字符编码，如果省略，则会使用运行Java程序的机器的“默认编码”，不同机器默认编码可能不同。

可以使用相对路径或者绝对路径。



**写入文件**

```java
PrintWriter out = new PrintWriter("myfile.txt","UTF-8");
```

如果文件不存在，则创建该文件。



🎈如果用一个不存在的文件构造一个Scannser，或者用一个不能被创建的文件名构造一个PrintWriter，就会发生各种异常。

此时，应该告知编译器：已经知道有可能出现“输入/输出”异常。需要 `throws IOException` 。

```java
public static void main(String[] args)throws ILException{
    Scanner in = new Scanner(Paths.get("myfile.txt"),"UTF-8");
    ...
}
```



### 3.8 控制流程



#### 3.8.1 块作用域



块（block）是由一对大括号括起来的若干条简单的Java语句。

块确定了变量的作用域。可以嵌套。但是，不能在嵌套的两个块中声明同名的变量。

```java
public static void main(String[] args){
    int n;
    ...
    {
        int k;//只能在块的范围内起作用。
        int n;//Error--不能在嵌套的两个块中声明同名的变量。
        ...
    }
}
```

#### 3.8.2 条件语句

```java
 if (condition) statement `  or   `if (condition) statement1 else statement2
```



#### 3.8.3 while循环

当条件为 true 时，while 循环执行一个语句块。`while (condition) statement`

![image.png](https://cdn.nlark.com/yuque/0/2020/png/641808/1585717641873-b8277365-c9a5-434f-b7b3-60afd22386b3.png)

while 语句的流程图

while语句放在前，首先检测循环条件。因此，循环体中的代码有可能不被执行。

如果希望循环体至少执行一次，则应该将检测条件放在最后。

使用do/while循环语句：`do statement while ()`



#### 3.8.4 确定循环--for循环

for循环

```java
for(int i=0; i>0; i--){
    System.out.println("Counting down..." + i);
    ...
}
```



for each 循环（通用 for 循环）`for (varibale : collection) statement`

```java
for(int element : a){
    System.out.println(element);
}//打印数组a的每一个元素
```

循环a中的每一个元素（for each element in a）。不了解数组具体有多少个元素或者数组的长度是可变动的时候，使用for each循环更加简洁。



#### 3.8.5 多重选择：switch语句



```java
int choice = in.nextInt();
switch(choice){
    case 1:
        ...
        break;
    case 2:
        ...
        break;
    case 3:
        ...
        break;
    default://bad input
        ...
        break;
}
```

💡如果case分支语句的末尾没有break语句，那么就会接着执行下一个case分支。

case的标签可以是：

+ char、byte、short、int 或 字符串字面量。
+ 枚举常量。



#### 3.8.6 中断控制流程语句

**break**

举一个例子，说明break语句的工作状态。

💡注意，标签必须放在希望跳出的最外层循环之前，并且必须紧跟一个冒号。只能跳出语句块，不能跳入。

```java
Scanner in = new Scanner(System.in);
int n;
read_data:
while(...){
    ...
    for(...){
        System.out.println("...");
        n = in.nextInt();
        if(n<0){
            break read_data;
        }
        ...
    }
}
```



**continue**

将控制转移到最内层循环的首部。

例如for循环中，遇到 continue 时，代码执行顺序直接跳转到for循环首部，下标加一继续循环。continue 后的代码语句将不执行。

continue也可以带标签，然后跳转到与标签匹配的循环首部。



### 3.9 大数值

Java.math 包中的两个类：`BigInter` 和 `BigDecimal`。这两个类可以处理包含任意长度数字序列的数值。



### 3.10 数组

数组是一种数据结构，用来存储同一类型值的集合。



**声明方式**：

+ `int[] a;`仅仅声明了变量a，没有初始化。
+ `int[] a = new int[100];`

创建并初始化：`int[] smallPrimes = {2, 5, 7, 11, 13};`这时就不用new。

也可以这样：`smallPrimes = new int[]{2, 5, 7, 11, 13};`

💡一旦创建数组，就不可以改变它的大小。如果需要在运行过程中扩展数组的大小，就应该使用另外一种数据结构——数组列表（arry list）。



**多维数组（二维数组、矩阵）**

初始化`double[][] balances = new double[行数][列数];`

或者不用 new

```java
int[][] magicSquare =
{
    {16, 3, 2, 13},
    {5, 10, 11, 8},
    {9, 6, 7, 12},
    {4, 15, 14, 1}
};
```

for each 不能自动处理二位数组的每一个元素。需要使用两个嵌套的循环。例如，要访问数组 a 的每一个元素。

```java
for(double row[] : a){
    for(double value : row){
        System.out.println(value);
        //do something with value
    }
}
```



## 四、对象与类



### 4.1 面向对象程序设计概述

面向对象程序设计（简称 OOP）。面向对象的程序是由对象组成的，每个对象包含对用户公开的特定功能部分和隐藏的实现部分。从根本上说，只要对象能够满足要求，就不必关心其功能的具体实现过程。在OOP中，不必关心对象的具体实现，只要能够满足用户的需求即可。



#### 4.1.1 类

**类（class）**是构造对象的模板或蓝图。

由类**构造（construct）**对象的过程称为创建类的**实例（instance）**。

**封装**（**encapsulation**，有时称为数据隐藏）是与对象有关的一个重要概念。形式上，封装将数据和行为组合在一个包中，并对对象的使用者隐藏了数据的实现方式。对象中的数据称为**实例域（instance field），**操纵数据的过程称为**方法（method）。**对于每个特定的类实例（对象）都有一组特定的实例域值。这些值的集合就是这个对象的当前**状态（state）**。



#### 4.1.2 对象

对象的三个主要特性：

+ 对象的行为（behavior）
+ 对象的状态（state）
+ 对象标识（identity）



#### 4.1.3 类之间的关系

最常见的关系有：依赖(dependence)、聚合(aggregation)、继承(inheritance)。



### 4.2 使用预定义类

#### 4.2.1 对象与对象变量

要想使用对象，就必须首先构造对象，并指定其初始状态。然后，对对象应用方法。

使用构造器（constructor）构造新实例。构造器是一种特殊的方法，用来构造并初始化对象。构造器的名字应该与类名相同。

对象与对象变量之间存在区别。对象变量需要初始化才可以使用方法，否则会报错。

一个对象变量并没有实际包含一个对象，而仅仅引用一个对象。

