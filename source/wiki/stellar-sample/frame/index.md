---
layout: wiki
wiki: stellar-sample
title: frame设备框架
---

## 基础用法


{% grid %}
<!-- cell -->
{% frame iphone11 设备顶部 img:/assets/logo.png video: focus:top %}

<!-- cell -->
{% frame iphone11 设备底部 img:/assets/logo.png video: focus:bottom %}

{% endgrid %}

### 语法格式

```markdown index.md
{% frame device [img:src] [video:url] [focus:top/bottom] [alt] %}
```

## 属性

| 属性名    | 说明              |
|--------|-----------------|
| device | 设备型号            |
| img    | 图片              |
| video  | 视频地址            |
| focus  | 聚焦位置 top/bottom |
| alt    | 描述文本            |

{% note color:yellow device 目前主题仅支持`iPhone11`，可通过自定义样式实现其他设备  %}
