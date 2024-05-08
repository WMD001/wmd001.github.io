---
layout: wiki
wiki: stellar-sample
title: note 备注块
---

## 基础用法

{% note 这是一个备注块 %}
{% note 这里设置标题 这是一个备注块 %}
{% note color:red red 设置color为<code>red</code> %}

{% folding child:codeblock open:false color:default 查看代码 %}

```markdown
{% note 这是一个备注块 %}
{% note 这里设置标题 这是一个备注块 %}
{% note color:red red 设置color为<code>red</code> %}
```

{% endfolding %}

### 语法格式

```markdown 
{% note title content [color:] %}
```

可以指定备注块的标题，内容和颜色。

## 具有标题的备注块

{% note 这里是标题 这里是备注块内容 %}
{% folding child:codeblock open:false color:default 查看代码 %}

```markdown
{% note 这里是标题 这里是备注块内容 %}
```

{% endfolding %}

## 彩色备注块

通过`color`属性设置颜色

{% note 一共支持12种颜色，可以满足几乎所有的需求了。 color 可设置
red、orange、amber、yellow、green、cyan、blue、purple、light、dark、warning、error 几种取值。 %}
{% note color:red red 设置color为<code>red</code> %}
{% note color:orange orange 设置color为<code>orange</code> %}
{% note color:amber amber 设置color为<code>amber</code> %}
{% note color:yellow yellow 设置color为<code>yellow</code> %}
{% note color:green green 设置color为<code>green</code> %}
{% note color:cyan cyan 设置color为<code>cyan</code> %}
{% note color:blue blue 设置color为<code>blue</code> %}
{% note color:purple purple 设置color为<code>purple</code> %}
{% note color:light light 设置color为<code>light</code> %}
{% note color:dark dark 设置color为<code>dark</code> %}
{% note color:warning warning 设置color为<code>warning</code> %}
{% note color:error error 设置color为<code>error</code> %}

{% folding child:codeblock open:false color:default 查看代码 %}

```markdown
{% note color:red red 设置color为<code>red</code> %}
{% note color:orange orange 设置color为<code>orange</code> %}
{% note color:amber amber 设置color为<code>amber</code> %}
{% note color:yellow yellow 设置color为<code>yellow</code> %}
{% note color:green green 设置color为<code>green</code> %}
{% note color:cyan cyan 设置color为<code>cyan</code> %}
{% note color:blue blue 设置color为<code>blue</code> %}
{% note color:purple purple 设置color为<code>purple</code> %}
{% note color:light light 设置color为<code>light</code> %}
{% note color:dark dark 设置color为<code>dark</code> %}
{% note color:warning warning 设置color为<code>warning</code> %}
{% note color:error error 设置color为<code>error</code> %}
```

{% endfolding %}

## 属性

| 参数      | 说明   |
|---------|------|
| title   | 标题   |
| content | 内容   |
| color   | 背景颜色 |
