---
layout: wiki
wiki: stellar-sample
title: copy复制行
---

## 基础用法

{% copy npm install prefix:shell %}
{% copy npm run server %}

{% folding child:codeblock open:false color:default 查看代码 %}

```markdown 
{% copy text [prefix:shell] %}

```

{% endfolding %}

### 语法格式

```markdown 
{% copy [git:] text [prefix:] %}
```

## 指定前缀

通过`prefix`参数可指定前缀
{% copy npm install prefix:$ %}
{% folding child:codeblock open:false color:default 查看代码 %}

```markdown 
{% copy npm install prefix:$ %}

```

{% endfolding %}

### 快速放置github仓库

设置`git:https`或者`git:ssh`或者`git:gh`来快速放置一个github仓库链接

{% copy git:https wmd001/wmd001 %}

{% folding child:codeblock open:false color:default 查看代码 %}

```markdown
{% copy git:https wmd001/wmd001 %}
```

{% endfolding %}

## 属性

| 属性名    | 说明      |
|--------|---------|
| text   | 内容      |
| prefix | 指定前缀    |
| git    | 指定git仓库 |
