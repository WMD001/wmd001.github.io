---
layout: wiki
wiki: stellar-sample
title: audio音频标签
---

## 基础用法

{% audio https://github.com/volantis-x/volantis-docs/releases/download/assets/Lumia1020.mp3 autoplay:1 %}
{% audio netease:1856385686 type:0 %}

{% folding child:codeblock open:false color:default 查看代码 %}

```markdown index.md
{% audio https://github.com/volantis-x/volantis-docs/releases/download/assets/Lumia1020.mp3 %}
{% audio netease:1856385686 %}
```

{% endfolding %}

### 语法格式

```markdown index.md
{% audio src [netease:] [type:2] [autoplay:0]  %}
```

## 支持网易云音乐

{% audio netease:1856385686 %}
`netease`指定网易云歌单/歌曲 id，`type` 设置歌曲/歌单 模式。默认为2歌曲模式

## 属性

| 属性名      | 说明             |
|----------|----------------|
| src      | 外链地址           |
| type     | 2/0 网易云歌曲/歌单模式 |
| netease  | 网易云歌曲/歌单 id    |
| autoplay | 1/0 是否开启自动播放   |
