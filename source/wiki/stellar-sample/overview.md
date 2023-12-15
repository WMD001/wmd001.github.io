---
mermaid: true
layout: wiki
wiki: stellar-components
---

{% quot el:h1 组件总览 %}

{% quot 表达类标签 %}

{% grid bg:block %}
<!-- cell left -->
[emoji表情]()

{% ablock color:blue %}

{% emoji 爱你 %} {% emoji blobcat ablobcatrainbow %} {% emoji blobcat ablobcatattentionreverse %} {% emoji tieba 滑稽 %}

{% endablock %}

<!-- cell right -->
[Mark行内文本标记](https://baidu.com)

{% ablock %}

{% mark 默认 %} {% mark 红 color:red %} {% mark 橙 color:orange %} {% mark 黄 color:yellow %} {% mark 绿 color:green %} 

{% endablock %}

{% endgrid %}


{% grid bg:block %}

<!-- cell left -->
[tag标签]()

{% ablock color:blue %}

{% tag Stellar https://xaoxuu.com/wiki/stellar/ %}
{% tag Hexo https://hexo.io/ %}
{% tag GitHub https://github.com/xaoxuu/ %}
{% tag Gitea https://git.xaox.cc/ color:green %}

{% endablock %}

<!-- cell right -->
[image图片标签]()

{% ablock color:blue %}



{% endablock %}

{% endgrid %}


{% grid bg:block %}

<!-- cell left -->

[quot引用]()

{% ablock color:blue %}

{% quot 个人博客 %}

{% endablock %}

<!-- cell right -->

[poetry诗词]()

{% ablock color:blue %}

{% poetry 游山西村 author:陆游 footer:诗词节选 %}
莫笑农家腊酒浑，丰年留客足鸡豚。
**山重水复疑无路，柳暗花明又一村。**
箫鼓追随春社近，衣冠简朴古风存。
从今若许闲乘月，拄杖无时夜叩门。
{% endpoetry %}

{% endablock %}

{% endgrid %}

{% grid bg:block %}

<!-- cell left -->

[note备注块]()

{% note 标题 这是一段备注块 %}

{% note color:blue 标题 这是一段彩色的备注块 %}

<!-- cell right -->

[link链接标签]()

{% link https://xaoxuu.com/blog/20221029/ desc:true %}

{% endgrid %}


{% grid bg:block %}

<!-- cell left -->

[Mermaid图表]()

```mermaid
graph LR
  A(Section A) -->|option 1| B(Section A)
  B -->|option 2| C(Section C)
```

<!-- cell right -->

{% endgrid %}

{% quot 数据集合类标签 %}

{% quot 容器类标签 %}

{% quot 表达类标签 %}


```mermaid
graph LR
  A(Section A) -->|option 1| B(Section A)
  B -->|option 2| C(Section C)
```