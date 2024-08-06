---
title: 原型模式
topic: design-pattern
tags: [设计模式]
categories: [设计模式]
date: 2024-08-05 21:28:18
description: 创建型设计模式之原型模式，亦称 克隆、Clone、Prototype
rightbar: [ghrepo, toc]
repo: WMD001/design-pattern-4j
---

## 意图

**原型模式**是一种创建型设计模式，使你能够复制已有对象，而又无需使代码依赖它们所属的类。

原型模式将克隆过程委派给被克隆的实际对象。模式为所有支持克隆的对象声明了一个通用接口，该接口让你能够克隆对象，同时又无需将代码和对象所属类耦合。
通常情况下，这样的接口中仅包含一个克隆方法。

## 原型模式结构

![img.png](img.png)

1. **原型** （Prototype） 接口将对克隆方法进行声明。 在绝大多数情况下， 其中只会有一个名为 clone克隆的方法。
2. **具体原型** （Concrete Prototype） 类将实现克隆方法。 除了将原始对象的数据复制到克隆体中之外， 该方法有时还需处理克隆过程中的极端情况， 例如克隆关联对象和梳理递归依赖等等。
3. **客户端** （Client） 可以复制实现了原型接口的任何对象。

## 实例

在java中实现原型模式非常简单，只需要让你的类实现`Cloneable`，并重写`clone`方法即可。

如下:

{% folding child:codeblock open:false color:default DataPrototype.class %}
```java 
public class DataPrototype implements Cloneable {

    private final Object data;

    public DataPrototype(DataPrototype dataPrototype) {
        this.data = dataPrototype.data;
    }

    @Override
    public DataPrototype clone() {
        DataPrototype dataPrototype;
        try {
            dataPrototype = (DataPrototype) super.clone();
        } catch (CloneNotSupportedException e) {
            dataPrototype = new DataPrototype(this);
        }
        return dataPrototype;
    }
}
```
{% endfolding %}

在此场景中，`Cloneable.class`为原型接口，`DataPrototype.class`为具体原型类，其实现了`Cloneable`的克隆方法。