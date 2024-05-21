---
title: 探究java中的模块化
tags: [java, 模块化]
categories: [后端]
date: 2024-05-21 09:14:08
description:
---

## 具名模块

先言，`java`模块化是`java`9之后才引入的，`java`8之前，`java`程序都是非模块化的。
java9将java中的基础类库，比如`java.base`，`java.logging`等，都单独拆分打包成模块。可以通过命令
{% copy java --list-modules prefix:$ %}
查看所有的模块。所有的`.jmod`文件，存放在`$JAVA_HOME/jmods`目录下。


### 1.创建模块
使用`idea`创建一个普通的`java`工程`module-A`，创建好的项目如下：
![](Untitled.png)

在src下新建`module_info.java`, 添加如下代码：
```java module_info.java
mavaodule module.A {
	// 依赖java.logging模块
    requires java.logging;
}
```

修改`Main.java`
```java Main.java
import java.util.logging.Logger;

public class Main {
    public static void main(String[] args) {
        Logger log = Logger.getLogger("Main");
        log.info("Hello World!");
    }
}
```

运行`Main.main`方法，启动失败：
![](Untitled1.png)

报错信息说的是无效的模块描述异常，Main.class在顶层目录下，而不在包下。那么我们在src下新建一个package叫做`top`，将`Main.java`移动到`top`包下，重新运行`Main.main`方法，成功运行。
![](Untitled2.png)

这样，我们通过给普通java工程添加`module_info.java`，就可以将java工程变成模块化项目。

### 2.打包模块

在我们运行`Main.main`方法之后，按照idea自动配置，输出class文件到`out/production/module-A`目录下，下一步，我们需要把class文件打包成jar包。
这里借助idea配置`artifact`，构建出jar包。
{% image img.png idea配置 %}

配置好之后，点击`Build Artifacts`，选择`module-A`，点击`Build`，即可生成jar包。
{% image img1.png out目录结构 %}

目前，生成的jar包还不能称之为模块。我们还需要一个工具`jmod`来打包成模块。
```shell 
cd out/artifaces/module_A_jar/
jmod create --class-path module-A.jar module-A.jmod
```
最终在jar包同级目录下生成一个`module-A.jmod`文件。这便是最终的模块。


### 3.运行模块

要运行一个jar，要使用`java -jar module-A.jar`，那么我们该如何运行一个模块呢，我们先看一下java命令
```shell
#: java
用法：java [options] <主类> [args...]
           （执行类）
   或  java [options] -jar <jar 文件> [args...]
           （执行 jar 文件）
   或  java [options] -m <模块>[/<主类>] [args...]
       java [options] --module <模块>[/<主类>] [args...]
           （执行模块中的主类）
   或  java [options] <源文件> [args]
           （执行单个源文件程序）

 将主类、源文件、-jar <jar 文件>、-m 或
 --module <模块>/<主类> 后的参数作为参数
 传递到主类。
 
 ...
```
可以看到，要执行模块中的主类，我们需要使用`-m`或者`--module`来指定模块和主类。
```shell
java -m module.A/top.Main
```
运行命令，发现报错：
![](img2.png)

错误信息是找不到`module.A`模块，加上`--module-path`参数，来指定我们的模块。
```shell 
java --module-path module-A.jmod -m module.A/top.Main
```
运行，还是报错
![img.png](img3.png)

原因是`.jmod`不能被放入`--module-path`中，换成`.jar`就没问题了。

```shell 
java --module-path module-A.jar -m module.A/top.Main
5月 21, 2024 10:50:20 上午 top.Main main
信息: Hello World!
```

也可以这样写：
```shell 
java --module-path ./ -m module.A/top.Main
5月 21, 2024 10:50:20 上午 top.Main main
信息: Hello World!
```
但我们要明白，具体起作用的是`.jar`文件，而不是`.jmod`文件。

那么我们打包出来的`.jmod`文件有什么用呢？答案是用来打包`jre`。


### 4.打包jre

`jlink`是java9之后提供的一个工具。官方说明：
{% note color:default jlink The `jlink` tool links a set of modules, along with their transitive dependences, to create a custom runtime image. %}

我们可以使用`jlink`打包jre来作为运行时环境。因为java9开始，java已经都实现了模块化，所以打包中可以只使用必须要的模块。
```shell
jlink --module-path module-A.jmod --add-modules java.base,java.logging,module.A --output jre/
```
`--module-path`参数指定模块的路径，`--add-modules`参数指定要打包的模块，多个模块使用`,`分隔。`--output`参数指定输出路径。

现在我们的目录下可以看到`jre`目录了。
![img.png](img4.png)

我们可以使用`jre`目录下的`bin/java`来直接运行我们的模块。而不需要再使用`--module-path`指定模块路径。
```shell
jre/bin/java -m module.A/top.Main
May 21, 2024 11:12:14 AM top.Main main
信息: Hello World!
```
如果我们要分发这个程序，只需要把jre目录打个压缩包即可。对方直接运行上边命令即可，不再需要安装java环境，也不需要知道如何配置模块，极大的方便了分发和部署。


### 5.module-info.java

回过头来，我们再看一下`module_info.java`文件。
```java module_info.java
module module.A {
	// 依赖java.logging模块
	requires java.logging;
}
```

`module_info.java`文件用来声明模块的依赖关系。`module`关键字声明模块。`requires`关键字用来声明依赖的模块。没有声明依赖的模块，是无法使用的。所有的模块默认都依赖`java.base`, 可省略不写。
那么如果我们要把创建的模块给其它模块使用，该如何写呢？我们可以看下`java.logging`模块的`module_info.java`文件。
```java module_info.java
module java.logging {
    exports java.util.logging;

    provides jdk.internal.logger.DefaultLoggerFinder with
        sun.util.logging.internal.LoggingProviderImpl;
}
```
可以看到，使用`exports`关键字来声明模块的导出包。`provides`关键字用来声明模块的提供者。
这里只声明导出了`java.util.logging`包，所以我们只能访问`java.util.logging`包，而不能访问其它包中的类。
简单说下`module-info.java`中的关键字。

#### module
模块声明。
```java module-info.java 
module moduleName{
}
```
模块声明的正文可以留空，也可以包含各种指令，比如`requires`、`exports`、`provides`等。

#### requires
指定此模块依赖于另一个模块，每个模块必须明确指出其依赖项。
```java module-info.java
requires moduelName;
```

#### requires static
用于指示在编译时必须要有模块，但运行时并不需要。


#### requires transitive
`requires transitive`关键字用来声明模块的依赖关系，并且会传递给依赖它的模块。例如A模块依赖B模块，B模块依赖C模块，那么使用`requires transitive`，A模块就可以直接使用C模块中的类。

#### exports
`exports`关键字用来声明模块的导出包。

#### exports...to
`exports...to`关键字用来声明模块的导出包，并且指定导出给哪些模块。

#### uses
`uses`关键字用来声明模块的接口。

#### provides...with
`provides`关键字用来声明模块的提供者。指令的 `with` 部分指定 `implements` 接口或 `extends abstract`类的服务提供类的名称。

#### open
模块本身可以被`open`修饰。表示该模块是开放的。

#### opens
`opens`关键字用来声明模块的开放包。

#### opens...to
`opens`关键字用来声明模块的开放包，并且指定开放给哪些模块。

## 不具名模块和自动模块

java9之后，jdk实现了模块化，那么我们是否也都需要模块化呢？答案是否定的。
{% mark color:yellow 我们依然可以延续以往的开发模式，而不使用模块化。 %}

使用idea重新创建一个java项目`module-B`。

{% image img_1.png module-B结构 %}

修改`Main.java`:
```java Main.java
import java.util.logging.Logger;

public class Main {
    public static void main(String[] args) {
        Logger logger = Logger.getLogger("Main");
        logger.info("Hello World!");
    }
}
```

运行`main`方法
{% image img_2.png 运行结果 %}

可以看到，没有`module-info.java`文件，依然可以使用`java.util.logging`包。
那么这个普通工程可以打包成模块吗？
我们来尝试一下。

首先，构建一个可执行的jar文件，然后借助`jmod`打包：
```shell
# 测试jar包可以正常执行
java -jar module-B.jar 
jmod create --class-path module-B.jar module-B.jmod
```

运行报错，找不到`module-info.class`文件
{% image img_3.png  jmod create --class-path module-B.jar module-B.jmod %}

可以看到，这样是不行的。但我们依然就可以使用java命令以模块的方式来运行`module-B.jar`;

```shell 
java --module-path module-B.jar -m module.B/top.Main
```
{% image img_4.png 模块方式运行 %}

实际上，没有`module-info.java`的jar包可以称之为 {% mark color:yellow 不具名模块 %}，不具名模块放在`module-path`中，则会变成{% mark color:yellow 自动模块 %}。
允许 Java 9 模块能引用到这些模块中的类。自动模块对外暴露所有的包并且能引用到其他所有模块的类，其他模块也能引用到自动模块的类。由于自动模块并不能声明模块名，那么 JDK 会根据 jar 包名来自动生成一个模块名以允许其他模块来引用。生成的模块名按以下规则生成：首先会移除文件扩展名以及版本号，然后使用".“替换所有非字母字符。
例如`module-B.jar`会生成名为`module.B`的模块名。


### 访问权限

模块化之后，访问权限发生了改变。对于具名模块而言，所有的类都是私有的，只有模块声明的包或类才能被其他模块访问。而对于自动模块而言，所有的包都对外暴露，和java9之前并没有什么不同。


## 参考
{% link https://www.liaoxuefeng.com/wiki/1252599548343744/1281795926523938 desc:true %}
{% link https://www.oracle.com/cn/corporate/features/understanding-java-9-modules.html desc:true %}
{% link https://developer.aliyun.com/article/618778 desc:true %}





















