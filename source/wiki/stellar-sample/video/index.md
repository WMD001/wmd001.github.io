---
layout: wiki
wiki: stellar-sample
title: video视频标签
---

## 基础用法

支持`bilibili`和视频外链，可设置最大宽度，bili可设置自动播放

{% video bilibili:BV1GP4y1d729 width:100% autoplay:0 %}


{% folding child:codeblock open:false color:default 查看代码 %}
```markdown index.md
{% video bilibili:BV1GP4y1d729 width:100% autoplay:0 %}
```

{% endfolding %}

### 语法格式

```markdown 
{% video bilibili:BV1GP4y1d729 width:100% autoplay:0 [type:] src  %}
```


## 属性

| 属性名      | 说明                 |
|----------|--------------------|
| type     | 外链类型，默认 video/mp4  |
| bilibili | bilibili 视频id      |
| ratio    | bilibili显示比例       |
| width    | 设置宽度 100% 800px    |
| autoplay | 1/0 bilibili是否自动播放 |
| src      | 外链地址               |
