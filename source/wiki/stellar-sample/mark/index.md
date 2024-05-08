---
layout: wiki
wiki: stellar-sample
title: Mark标记标签
---

## 基础用法

{% mark 这是一段标记文本 %}
{% mark 这是一段红色文本 color:red %}
{% mark 这是一段橙色文本 color:orange %}

{% folding child:codeblock open:false color:default 查看代码 %}
```markdown
{% mark 这是一段标记文本 %}
{% mark 这是一段红色文本 color:red %}
{% mark 这是一段橙色文本 color:orange %}
```
{% endfolding %}

### 语法格式

```markdown 
{% mark text [color] %}
```

## 彩色标记

包括：{% mark 默认 %} {% mark 红 color:red %} {% mark 橙 color:orange %} {% mark 黄 color:yellow %} {% mark 绿 color:green %} {% mark 青 color:cyan %} {% mark 蓝 color:blue %} {% mark 紫 color:purple %} {% mark 亮 color:light %} {% mark 暗 color:dark %} {% mark 警告 color:warning %} {% mark 错误 color:error %} 一共 12 种颜色

{% folding child:codeblock open:false color:default 查看代码 %}

```markdown
包括：{% mark 默认 %} {% mark 红 color:red %} {% mark 橙 color:orange %} {% mark 黄 color:yellow %} {% mark 绿 color:green %} {% mark 青 color:cyan %} {% mark 蓝 color:blue %} {% mark 紫 color:purple %} {% mark 亮 color:light %} {% mark 暗 color:dark %} {% mark 警告 color:warning %} {% mark 错误 color:error %} 一共 12 种颜色
```

{% endfolding %}


## 属性

| 参数    | 说明                                                                                              |
|-------|-------------------------------------------------------------------------------------------------|
| text  | 标记文本                                                                                            |
| color | red \| orange \| yellow \| green \| cyan \| blue \| purple \| light \| dark \| warning \| error |
