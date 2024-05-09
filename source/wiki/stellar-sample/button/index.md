---
layout: wiki
wiki: stellar-sample
title: button按钮
---

## 基础用法

{% button 探索 https://github.com/xaoxuu/hexo-theme-stellar/ icon:solar:planet-bold-duotone %}
{% button 微信 https://wechat.com icon:share:wechat %}
{% button 微博 https://weibo.com icon:share:weibo %}
{% folding child:codeblock open:false color:default 查看代码 %}

{% endfolding %}

### 语法格式

```markdown 
{% button text url [icon:] [color:] [size:xs] %}
```

## 属性

| 属性名   | 说明                             |
|-------|--------------------------------|
| text  | 显示文本                           |
| url   | 跳转链接                           |
| color | 颜色                             |
| icon  | 显示图标，支持 icons.yml 中的配置名称和外链图标  |
| size  | 尺寸大小，目前只有两种尺寸：默认是普通大小， xs 是最小号 |
