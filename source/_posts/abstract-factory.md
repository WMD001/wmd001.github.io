---
title: 抽象工厂
topic: design-pattern
tags: [设计模式]
categories: [设计模式]
date: 2024-07-01 17:20:19
description: 创建型设计模式之抽象工厂模式
rightbar: [ghrepo, toc]
repo: WMD001/design-pattern-4j
---

## 意图
**抽象工厂模式**是一种创建型设计模式， 它能创建一系列相关的对象， 而无需指定其具体类。

## 抽象工厂模式结构

![img.png](img.png)

1. **抽象产品** （Abstract Product） 为构成系列产品的一组不同但相关的产品声明接口。
2. **具体产品** （Concrete Product） 是抽象产品的多种不同类型实现。 所有变体 （维多利亚/现代） 都必须实现相应的抽象产品 （椅子/沙发）。
3. **抽象工厂** （Abstract Factory） 接口声明了一组创建各种抽象产品的方法。
4. **具体工厂** （Concrete Factory） 实现抽象工厂的构建方法。 每个具体工厂都对应特定产品变体， 且仅创建此种产品变体。
5. 尽管具体工厂会对具体产品进行初始化， 其构建方法签名必须返回相应的抽象产品。 这样， 使用工厂类的客户端代码就不会与工厂创建的特定产品变体耦合。 客户端 （Client） 只需通过抽象接口调用工厂和产品对象， 就能与任何具体工厂/产品变体交互。

## 实例
好的，我们来设计一个更贴近实际工作中可能会用到的抽象工厂模式示例。假设我们正在开发一个跨平台的应用程序，这个应用程序需要支持不同的数据库（例如，MySQL 和 Oracle）。我们可以使用抽象工厂模式来创建数据库连接和执行查询。

### 1. 定义产品接口

首先定义两个产品接口：`DBConnection` 和 `DBCommand`。

```java
// DBConnection.java
public interface DBConnection {
    void connect();
}

// DBCommand.java
public interface DBCommand {
    void execute(String query);
}
```

### 2. 定义具体产品实现

然后创建具体的产品实现类，针对 MySQL 和 Oracle。

```java
// MySQLConnection.java
public class MySQLConnection implements DBConnection {
    @Override
    public void connect() {
        System.out.println("Connecting to MySQL database...");
    }
}

// OracleConnection.java
public class OracleConnection implements DBConnection {
    @Override
    public void connect() {
        System.out.println("Connecting to Oracle database...");
    }
}

// MySQLCommand.java
public class MySQLCommand implements DBCommand {
    @Override
    public void execute(String query) {
        System.out.println("Executing MySQL query: " + query);
    }
}

// OracleCommand.java
public class OracleCommand implements DBCommand {
    @Override
    public void execute(String query) {
        System.out.println("Executing Oracle query: " + query);
    }
}
```

### 3. 定义抽象工厂接口

接下来定义抽象工厂接口。

```java
// DBFactory.java
public interface DBFactory {
    DBConnection createConnection();
    DBCommand createCommand();
}
```

### 4. 定义具体工厂实现

然后创建具体的工厂实现类，针对 MySQL 和 Oracle。

```java
// MySQLFactory.java
public class MySQLFactory implements DBFactory {
    @Override
    public DBConnection createConnection() {
        return new MySQLConnection();
    }

    @Override
    public DBCommand createCommand() {
        return new MySQLCommand();
    }
}

// OracleFactory.java
public class OracleFactory implements DBFactory {
    @Override
    public DBConnection createConnection() {
        return new OracleConnection();
    }

    @Override
    public DBCommand createCommand() {
        return new OracleCommand();
    }
}
```

### 5. 客户端代码

最后是客户端代码，通过传入不同的工厂来创建不同的数据库连接和执行查询。

```java
// Client.java
public class Client {
    private DBConnection connection;
    private DBCommand command;

    public Client(DBFactory factory) {
        connection = factory.createConnection();
        command = factory.createCommand();
    }

    public void run() {
        connection.connect();
        command.execute("SELECT * FROM users");
    }

    public static void main(String[] args) {
        DBFactory factory;

        // For MySQL
        factory = new MySQLFactory();
        Client client1 = new Client(factory);
        client1.run();

        // For Oracle
        factory = new OracleFactory();
        Client client2 = new Client(factory);
        client2.run();
    }
}
```

### 运行结果

```
Connecting to MySQL database...
Executing MySQL query: SELECT * FROM users
Connecting to Oracle database...
Executing Oracle query: SELECT * FROM users
```

在这个示例中，客户端代码使用了抽象工厂模式来创建数据库连接和执行查询的对象。通过传入不同的工厂实例（`MySQLFactory` 或 `OracleFactory`），客户端可以在运行时选择使用不同的数据库，而不需要改变客户端代码。这种方式使得系统更具可扩展性和可维护性，可以轻松地支持更多种类的数据库。

{% link https://github.com/WMD001/design-pattern-4j/tree/main/src/main/java/top/wmd001/creational/abstract_factory 源码地址 desc:false %}