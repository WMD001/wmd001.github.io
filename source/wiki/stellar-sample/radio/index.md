---
layout: wiki
wiki: stellar-sample
title: radio单选
---

## 基础用法

{% radio 默认不勾选 %}
{% radio checked:false 没有勾选的单选框 %}
{% radio checked:true color:yellow 已勾选的单选框 %}

{% folding child:codeblock open:false color:default 查看代码 %}

```markdown
{% radio 默认不勾选 %}
{% radio checked:false 没有勾选的单选框 %}
{% radio checked:true color:yellow 已勾选的单选框 %}
```

{% endfolding %}

### 语法格式

```markdown index.md
{% radio [checked:false] [color:yellow] text %}
```

## 属性

| 属性名     | 说明    |
|---------|-------|
| checked | 是否选中  |
| color   | 单选框颜色 |
| text    | 显示文本  |

