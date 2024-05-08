---
layout: wiki
wiki: stellar-sample
title: poetry诗词
---

## 基础用法

{% poetry 离思五首·其四 author:元稹 date:唐 footer:唐诗 %}
曾经沧海难为水，除却巫山不是云。
{% emp 取次花丛懒回顾，半缘修道半缘君。 %}
{% endpoetry %}

{% folding child:codeblock open:false color:default 查看代码 %}
```markdown
{% poetry 离思五首·其四 author:元稹 date:唐 footer:唐诗 %}
曾经沧海难为水，除却巫山不是云。
{% emp 取次花丛懒回顾，半缘修道半缘君。 %}
{% endpoetry %}
```

{% endfolding %}

### 语法格式
```markdown 
{% poetry title [author:] [date:] [footer:] %}

[content]

{% endpoetry %}
```

## 属性

| 属性名     | 说明               |
|---------|------------------|
| title   | 标题               |
| author  | 作者               |
| date    | 时代               |
| footer  | 脚标               |
| content | 内容，可允许markdown语法 |
