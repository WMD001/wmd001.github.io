---
title: 工厂方法
topic: design-pattern
tags: [设计模式]
categories: [设计模式]
date: 2024-06-07 16:15:15
description: 创建型设计模式之工厂方法模式
---

## 意图
**工厂方法模式**定义一个用于创建对象的接口， 让子类决定实例化哪一个类。 工厂方法使一个类的实例化延迟到其子类。

## 工厂方法模式结构
![img.png](img.png)

1. **产品**(Product) 将会对接口进行声明。 对于所有由创建者及其子类构建的对象， 这些接口都是通用的。
2. **具体产品**(Concrete Products) 是产品接口的不同实现。
3. **创建者**(Creator) 类声明返回产品对象的工厂方法。 该方法的返回对象类型必须与产品接口相匹配。 你可以将工厂方法声明为抽象方法， 强制要求每个子类以不同方式实现该方法。 或者， 你也可以在基础工厂方法中返回默认产品类型。注意， 尽管它的名字是创建者， 但它最主要的职责并不是创建产品。 一般来说， 创建者类包含一些与产品相关的核心业务逻辑。 工厂方法将这些逻辑处理从具体产品类中分离出来。 打个比方， 大型软件开发公司拥有程序员培训部门。 但是， 这些公司的主要工作还是编写代码， 而非生产程序员。
4. **具体创建者**(Concrete Creators) 将会重写基础工厂方法， 使其返回不同类型的产品。 注意， 并不一定每次调用工厂方法都会创建新的实例。 工厂方法也可以返回缓存、 对象池或其他来源的已有对象。

## 实例

假设我们正在开发一个用于检测数据库连接的程序, 该程序需要连接到不同的数据库系统。 我们可以使用工厂方法模式来实现这一点。

首先，定义一个数据库连接的接口，这样可以确保所有数据库连接实现都遵循相同的操作规范。
{% folding child:codeblock open:false color:default DatabaseConnection.java %}
```java DatabaseConnection.java
package main.java.top.wmd001.creational.factory_method;

public interface DatabaseConnection {

    void connect(String url, String username, String password);

    void disconnect();

}
```
{% endfolding %}

接着，为MySQL数据库创建一个连接的实现类。
{% folding child:codeblock open:false color:default MysqlConnection.java %}
```java MysqlConnection.java
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.SQLException;

public class MySqlConnection implements DatabaseConnection {
    private Connection connection;

    @Override
    public void connect(String url, String username, String password) {
        try {
            Class.forName("com.mysql.cj.jdbc.Driver");
            connection = DriverManager.getConnection(url, username, password);
            System.out.println("Connected to MySQL database.");
        } catch (ClassNotFoundException | SQLException e) {
            e.printStackTrace();
        }
    }

    @Override
    public void disconnect() {
        try {
            if (connection != null && !connection.isClosed()) {
                connection.close();
                System.out.println("Disconnected from MySQL database.");
            }
        } catch (SQLException e) {
            e.printStackTrace();
        }
    }
}
```

{% endfolding %}

然后，为Oracle数据库创建一个连接的实现类。

{% folding child:codeblock open:false color:default OracleConnection.java %}
```java OracleConnection.java
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.SQLException;

public class OracleConnection implements DatabaseConnection {
    private Connection connection;

    @Override
    public void connect(String url, String username, String password) {
        try {
            Class.forName("oracle.jdbc.driver.OracleDriver");
            connection = DriverManager.getConnection(url, username, password);
            System.out.println("Connected to Oracle database.");
        } catch (ClassNotFoundException | SQLException e) {
            e.printStackTrace();
        }
    }

    @Override
    public void disconnect() {
        try {
            if (connection != null && !connection.isClosed()) {
                connection.close();
                System.out.println("Disconnected from Oracle database.");
            }
        } catch (SQLException e) {
            e.printStackTrace();
        }
    }
}
```

{% endfolding %}

接下来，创建一个基础工厂, 它将负责创建具体的数据库连接实现。
{% folding child:codeblock open:false color:default DatabaseConnectionFactory.java %}
```java DatabaseConnectionFactory.java
package main.java.top.wmd001.creational.factory_method;

public interface DatabaseConnectionFactory {

    DatabaseConnection createConnection();

}

```
{% endfolding %}

然后是MySQL数据库连接工厂的实现。
{% folding child:codeblock open:false color:default MySqlConnectionFactory.java %}
```java MysqlConnectionFactory.java
package main.java.top.wmd001.creational.factory_method;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.SQLException;

public class MysqlConnection implements DatabaseConnection {

    private Connection connection;

    @Override
    public void connect(String url, String username, String password) {
        try {
            Class.forName("com.mysql.cj.jdbc.Driver");
            connection = DriverManager.getConnection(url, username, password);
            System.out.println("Connected to MySQL database.");
        } catch (ClassNotFoundException | SQLException e) {
            e.printStackTrace();
        }
    }


    @Override
    public void disconnect() {
        try {
            if (connection != null && !connection.isClosed()) {
                connection.close();
                System.out.println("Disconnected from MySQL database.");
            }
        } catch (SQLException e) {
            e.printStackTrace();
        }
    }
}
```
{% endfolding %}

还有Oracle数据库连接工厂的实现。
{% folding child:codeblock open:false color:default OracleConnectionFactory.java %}
```java OracleConnectionFactory.java
package main.java.top.wmd001.creational.factory_method;

/**
 * Create by habit on 2024/6/26
 */
public class OracleConnectionFactory implements DatabaseConnectionFactory {
    @Override
    public DatabaseConnection createConnection() {
        return new OracleConnection();
    }
}

```
{% endfolding %}

最后，创建一个客户端程序，用于测试工厂方法模式。
{% folding child:codeblock open:false color:default Client.java %}
```java Client.java
package main.java.top.wmd001.creational.factory_method;

public class Client {

    public static void main(String[] args) {
        DatabaseConnectionFactory factory = new MysqlConnectionFactory();
        DatabaseConnection connection = factory.createConnection();
        connection.connect("jdbc:mysql://localhost:3306/test", "root", "123456");
        connection.disconnect();

        factory = new OracleConnectionFactory();
        connection = factory.createConnection();
        connection.connect("jdbc:oracle:thin:@localhost:1521:orcl", "scott", "tiger");
        connection.disconnect();

    }

}
```

{% endfolding %}

以上, `DatabaseConnection`对应的是抽象产品，`DatabaseConnectionFactory`对应抽象工厂，`MysqlConnection`和`OracleConnection`对应具体产品，`MysqlConnectionFactory`和`OracleConnectionFactory`对应具体工厂。
