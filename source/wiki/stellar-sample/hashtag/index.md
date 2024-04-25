---
layout: wiki
wiki: stellar-sample
title: hashtag标签
---

## 基础用法

{% tabs %}
<!-- tab 效果 -->
{% hashtag Hexo %} {% hashtag Github https:github.com %} {% hashtag Node.js color:red %}

<!-- tab 代码 -->
```
{% hashtag Hexo %} {% hashtag Github %} {% hashtag Node.js %}
```

{% endtabs %}

共有`'red', 'orange', 'yellow', 'green', 'cyan', 'blue', 'purple'`7种颜色，在不指定颜色的情况下按照标签数量下标进行渲染，例如第一个hashtag颜色是`red`，第二个是`orange`等，也可在配置文件中设置`defautl_color`，设置后，所有标签都使用默认颜色

```yaml _config.stellar.yml
tag_plugins:
    hashtag:
        default_color: blue
```

## 属性

|参数|说明|
|:---:|:---:|
|text|文本|
|href|链接|
|color|'red', 'orange', 'yellow', 'green', 'cyan', 'blue', 'purple'|