---
layout: wiki
wiki: stellar-sample
title: quot 引用
---

## 效果示例

适合居中又醒目的标题

{% quot 不夜侯 %}

支持自定义引号：

{% quot icon:hashtag 不夜侯 %}

其中自定义引号素材在主题配置文件的`tag_plugins.quot`中配置：

{% box _config-stellar.yml %}

```yaml
tag_plugins:
  quot:
    default: # 可以自行配置多种图标方案
      prefix: https://bu.dusays.com/2022/10/24/63567d3e092ff.png
      suffix: https://bu.dusays.com/2022/10/24/63567d3e0ab55.png
    hashtag:
      prefix: https://bu.dusays.com/2022/10/24/63567d3e07da3.png
    quote:
      prefix: https://bu.dusays.com/2022/10/24/63567d3e092ff.png
      suffix: https://bu.dusays.com/2022/10/24/63567d3e0ab55.png
```

{% endbox %}

### 使用任意图标

从 1.26.5 版本开始，您可以通过 prefix 或 suffix 参数设置任意图标或图片，支持 URL 或 icons.yml 文件中配置，例如：

{% quot prefix:ph:seal-question-fill 图标示例 %}

## 参数说明

|参数|说明|
|---|---|
|el|设置作为标题，可选值：h2 \| h3 \| h4 \| h5 |
|icon|设置引号，默认为：default，取配置文件`tag_plugins.quot`|
|prefix|设置前引号|
|suffix|设置后引号|