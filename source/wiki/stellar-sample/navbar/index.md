---
layout: wiki
wiki: stellar-sample
title: navbar导航栏
---

## 基础用法

{% navbar [文章](/) [项目](/wiki/) [GitHub](https://github.com) active:/ %}

{% folding child:codeblock open:false color:default 查看代码 %}

```markdown index.md
{% navbar [文章](/) [项目](/wiki/) [GitHub](https://github.com) active:/ %}
```

{% endfolding %}

### 语法格式

```markdown index.md
{% navbar link ... active:active %}
```

## 属性

| 属性名    | 说明        |
|--------|-----------|
| link   | 超链接 可以有多个 |
| active | 当前激活的链接   |
