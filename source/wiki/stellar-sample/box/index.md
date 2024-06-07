---
layout: wiki
wiki: stellar-sample
title: box盒子容器
---

## 基础用法

{% grid %}
<!-- cell -->

{% box color:yellow child:codeblock %}

```java
public static void main(String[] args) {
    System.out.println("Hello World!");
}
```

{% endbox %}

<!-- cell -->

{% box color:green child:tabs box盒子容器 %}
容器里边的内容可以 {% mark color:yellow 嵌套 %} 其它标签
{% endbox %}

{% endgrid %}

{% folding child:codeblock open:false color:default 查看代码 %}

```markdown

{% box color:yellow child:codeblock %}

```java
public static void main(String[] args) {
    System.out.println("Hello World!");
}

{% endbox %}


{% box color:green child:tabs box盒子容器 %}
容器里边的内容可以 {% mark color:yellow 嵌套 %} 其它标签
{% endbox %}
```

{% endfolding %}

### 语法格式

```markdown index.md
{% box [title] [color:color] [child:codeblock/tabs] %}
...
{% endbox %}
```

## 属性

| 属性名   | 说明     |
|-------|--------|
| color | 容器颜色   |
| child | 容器内容类型 |
| title | 容器标题   |
