---
title: 桥接模式
tags: [设计模式]
categories: [设计模式]
date: 2024-09-19 23:39:22
description: 结构型设计模式之桥接模式
---

## 意图
**桥接模式**是一种结构型设计模式，可将一个大类或一系列相关的类拆分成抽象和实现两个独立的层次结构，从而能在开发时分别使用。

## 桥接模式结构

![img.png](img.png)

1. **抽象部分** （Abstraction） 提供高层控制逻辑， 依赖于完成底层实际工作的实现对象。
2. **实现部分** （Implementation） 为所有具体实现声明通用接口。 抽象部分仅能通过在这里声明的方法与实现对象交互。 抽象部分可以列出和实现部分一样的方法， 但是抽象部分通常声明一些复杂行为， 这些行为依赖于多种由实现部分声明的原语操作。
3. **具体实现** （Concrete Implementations） 中包括特定于平台的代码。
4. **精确抽象** （Refined Abstraction） 提供控制逻辑的变体。 与其父类一样， 它们通过通用实现接口与不同的实现进行交互。
5. 通常情况下， **客户端** （Client） 仅关心如何与抽象部分合作。 但是， 客户端需要将抽象对象与一个实现对象连接起来。

## 实例

假设我们需要在京东、淘宝两个平台的商铺上进行采购，而支付方式有微信和支付宝。使用桥接模式设计如下

### 1. 抽象部分

分别创建支付方式的抽象类 `PayWay.java` 和平台商铺的抽象类 `Store.java`

{% folding child:codeblock open:false color:default PayWay.java %}
```java 
package main.java.top.wmd001.structural.bridge.pay;

public interface PayWay {

    void pay(int money);

}

```

{% endfolding %}


{% folding child:codeblock open:false color:default Store.java %}
```java 
package main.java.top.wmd001.structural.bridge.store;

import main.java.top.wmd001.structural.bridge.pay.PayWay;

public abstract class Store {

    protected PayWay payWay;

    /**
     * 使用组合的方式关联PayWay
     * Store的子类也可以关联PayWay的子类
     * @param payWay PayWay
     */
    public Store(PayWay payWay) {
        this.payWay = payWay;
    }

    public abstract void pay(int money);

}

```

{% endfolding %}


### 2. 支付方式实现

微信支付

{% folding child:codeblock open:false color:default WeChatPay.java %}
```java 
package main.java.top.wmd001.structural.bridge.pay;

public class WeChatPay implements PayWay{
    @Override
    public void pay(int money) {
        System.out.println("使用微信支付成功！");
    }
}

```

{% endfolding %}

支付宝支付

{% folding child:codeblock open:false color:default AliPay.java %}
```java 
package main.java.top.wmd001.structural.bridge.pay;

public class AliPay implements PayWay{

    @Override
    public void pay(int money) {
        System.out.println("使用支付宝支付成功");
    }
}

```

{% endfolding %}

### 3. 平台商铺实现

京东平台

{% folding child:codeblock open:false color:default JdStore.java %}
```java 
package main.java.top.wmd001.structural.bridge.store;

import main.java.top.wmd001.structural.bridge.pay.PayWay;

public class JdStore extends Store {

    public JdStore(PayWay payWay) {
        super(payWay);
    }

    @Override
    public void pay(int money) {
        System.out.println("京东店铺消费：￥" + money);
        payWay.pay(money);
    }
}

```

{% endfolding %}

淘宝平台

{% folding child:codeblock open:false color:default TbStore.java %}
```java 
package main.java.top.wmd001.structural.bridge.store;

import main.java.top.wmd001.structural.bridge.pay.PayWay;

public class TbStore extends Store {

    public TbStore(PayWay payWay) {
        super(payWay);
    }

    @Override
    public void pay(int money) {
        System.out.println("淘宝店铺消费：￥" + money);
        payWay.pay(money);
    }
}

```

{% endfolding %}

### 4. 客户端测试

{% folding child:codeblock open:false color:default Client.java %}
```java 
package main.java.top.wmd001.structural.bridge;

import main.java.top.wmd001.structural.bridge.pay.AliPay;
import main.java.top.wmd001.structural.bridge.pay.WeChatPay;
import main.java.top.wmd001.structural.bridge.store.JdStore;
import main.java.top.wmd001.structural.bridge.store.Store;
import main.java.top.wmd001.structural.bridge.store.TbStore;

public class Client {


    public static void main(String[] args) {
        Store jdStore = new JdStore(new WeChatPay());
        jdStore.pay(1000);

        Store tbStore = new TbStore(new AliPay());
        tbStore.pay(1000);


    }

}

```

{% endfolding %}

输出结果

```text 
京东店铺消费：￥1000
使用微信支付成功！
淘宝店铺消费：￥1000
使用支付宝支付成功
```

在桥接模式中，由于抽象和实现是独立的，所有如果有新的平台商铺和新的支付方式时，只需要扩展子类，就可以实现新的组合方式。