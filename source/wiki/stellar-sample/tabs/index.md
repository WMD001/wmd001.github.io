---
layout: wiki
wiki: stellar-sample
title: tabs分栏容器
---

## 基础用法

{% tabs align:center active:1 %}
<!-- tab tab1 -->
这里是tab1

<!-- tab tab2 -->
这里是tab2

{% endtabs %}

{% folding child:codeblock open:false color:default 查看代码 %}

```markdown index.md
{% tabs align:left active:1 %}
<!-- tab tab1 -->
这里是tab1

<!-- tab tab2 -->
这里是tab2

{% endtabs %}
```

{% endfolding %}

### 语法格式

```markdown 
{% tabs [align:center] [active:1] %}
<!-- tab 标题 -->
内容

<!-- tab 标题 -->
内容

{% endtabs %}
```
`tabs`中可以嵌套其它标签或`markdown`文本。使用`active:1`指定默认激活标签。


## 属性

| 属性     | 说明      |
|--------|---------|
| align  | 对齐方式    |
| active | 当前选项卡索引 |
