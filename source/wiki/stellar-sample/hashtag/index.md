---
layout: wiki
wiki: stellar-sample
title: hashtag标签
---

## 基础用法

{% hashtag Hexo %} {% hashtag Github https:github.com %} {% hashtag Node.js color:red %}
{% folding child:codeblock open:false color:default 查看代码 %}

```markdown
{% hashtag Hexo %} {% hashtag Github https:github.com %} {% hashtag Node.js color:red %}
```

{% endfolding %}

### 语法格式

```markdown 
{% hashtag text [href] [color] %}
```

可以指定`href`使其具有超链接效果，也可以指定颜色

## 超链接效果

{% hashtag Hexo https://hexo.io %}
{% folding child:codeblock open:false color:default 查看代码 %}

```markdown
{% hashtag Hexo https://hexo.io %}
```

{% endfolding %}

## 自定义颜色

{% hashtag GitHub color:blue%}

{% folding child:codeblock open:false color:default 查看代码 %}

```markdown
{% hashtag GitHub color:blue%}
```

{% endfolding %}

共有`'red', 'orange', 'yellow', 'green', 'cyan', 'blue', 'purple'`
7种颜色，在不指定颜色的情况下按照标签数量下标进行渲染，例如第一个hashtag颜色是`red`，第二个是`orange`
等，也可在配置文件中设置`defautl_color`，设置后，所有标签都使用默认颜色

```yaml _config.stellar.yml
tag_plugins:
  hashtag:
    default_color: blue
```

## 属性

|  参数   |                              说明                              |
|:-----:|:------------------------------------------------------------:|
| text  |                             文本内容                             |
| href  |                             链接地址                             |
| color | 'red', 'orange', 'yellow', 'green', 'cyan', 'blue', 'purple' |