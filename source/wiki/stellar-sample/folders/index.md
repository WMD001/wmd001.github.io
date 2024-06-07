---
layout: wiki
wiki: stellar-sample
title: folders多个折叠容器聚合
---

## 基础用法

{% folders color:green %}
<!-- folder 题目1 -->
这是答案1
<!-- folder 题目2 -->
这是答案2
<!-- folder 题目3 -->
这是答案3
{% endfolders %}

{% folding child:codeblock open:false color:default 查看代码 %}

```markdown index.md 
{% folders color:green %}
<!-- folder 题目1 -->
这是答案1
<!-- folder 题目2 -->
这是答案2
<!-- folder 题目3 -->
这是答案3
{% endfolders %}
```

{% endfolding %}

### 语法格式

```markdown folders
{% folders [color:color] %}
<!-- folder title -->
content

{% endfolders %}
```

## 属性

| 属性名     | 说明         |
|---------|------------|
| title   | 折叠容器标题     |
| color   | 折叠容器标题颜色   |
| content | 折叠内容，可嵌套标签 |
