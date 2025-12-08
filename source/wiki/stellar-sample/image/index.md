---
layout: wiki
wiki: stellar-sample
title: image图片标签
---

## 基础用法

{% image https://staticre.deepal.com.cn/20231107-office/office/assets/ica/pc/redpoint.jpg 深蓝sl03 download:true fancybox:true ratio:1920/1080 %}

{% folding child:codeblock open:false color:default 查看代码 %}
```markdown
{% image https://staticre.deepal.com.cn/20231107-office/office/assets/ica/pc/redpoint.jpg 深蓝sl03 download:true fancybox:true ratio:1920/1080 %}
```

{% endfolding %}

### 语法格式

```markdown
{% image src [description] [download:bool/string] [width:px] [padding:px] [bg:hex] [fancybox:bool] %}
```

图片标签是一个精心设计的应对各种各种尺寸插图的标签，支持各种尺寸的图片，并且支持图片描述、下载、缩放功能。
默认使用图片将横向铺满。

## 属性

| 属性名         | 说明            |
|-------------|---------------|
| src         | 图片地址          |
| description | 图片描述          |
| download    | true \| 下载地址  |
| width       | 图片宽度          |
| padding     | 图片四周填充宽度      |
| bg          | 图片区域背景颜色，16进制 |
| fancybox    | 是否开启缩放功能      |
