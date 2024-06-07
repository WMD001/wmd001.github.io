---
layout: wiki
wiki: stellar-sample
title: folding折叠容器
---

## 基础用法

{% folding child:codeblock open:true color:default 查看代码 %}

```python 
print('hello world')
```

{% endfolding %}


{% folding child:codeblock open:false color:default 查看代码 %}

```markdown

{% folding child:codeblock open:true color:default 查看代码 %}


{% endfolding %}
```

{% endfolding %}

### 语法格式

```markdown index.md
{% folding title [child:codeblock] [open:bool] [color:color] %}
content
{% endfolding %}
```

## 属性

| 属性名   | 说明                  |
|-------|---------------------|
| title | 标题                  |
| child | codeblock/tabs 类型样式 |
| open  | 是否默认打开              |
| color | 颜色                  |
