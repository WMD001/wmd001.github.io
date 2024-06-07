---
layout: wiki
wiki: stellar-sample
title: checkbox复选框
---

## 基础用法

{% checkbox 默认复选框 %}
{% checkbox checked:true 已勾选的复选框 %}
{% checkbox checked:true color:red 设置颜色的复选框 %}
{% checkbox checked:true color:green symbol:plus 显示为加号的绿色的已勾选的复选框 %}
{% checkbox checked:true color:yellow symbol:minus 显示为减号的黄色的已勾选的复选框 %}
{% checkbox checked:true color:red symbol:times 显示为乘号的红色的已勾选的复选框 %}

{% folding child:codeblock open:false color:default 查看代码 %}

```markdown index.md
{% checkbox 默认复选框 %}
{% checkbox checked:true 已勾选的复选框 %}
{% checkbox checked:true color:red 设置颜色的复选框 %}
{% checkbox checked:true color:green symbol:plus 显示为加号的绿色的已勾选的复选框 %}
{% checkbox checked:true color:yellow symbol:minus 显示为减号的黄色的已勾选的复选框 %}
{% checkbox checked:true color:red symbol:times 显示为乘号的红色的已勾选的复选框 %}
```

{% endfolding %}

### 语法格式

```markdown index.md
{% checkbox checked:false color:default symbol:default text %}
```

## 属性

| 属性名     | 说明               |
|---------|------------------|
| checked | 复选框是否选中          |
| color   | 复选框颜色            |
| symbol  | plus/minus/times |
| text    | 显示文本             |
