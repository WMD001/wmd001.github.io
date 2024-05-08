---
layout: wiki
wiki: stellar-sample
title: icon图标标签
---

## 基础用法

{% icon default:goback %}
{% icon default:leftbar %}
{% icon default:rightbar %}
{% icon solar:planet-bold-duotone %}

{% folding child:codeblock open:false color:default 查看代码 %}

```markdown
{% icon default:goback %}
{% icon default:leftbar %}
{% icon default:rightbar %}
{% icon solar:planet-bold-duotone %}
```

{% endfolding %}

### 语法格式

```markdown
{% icon key [text] [color] [style] %}
```

支持在任意位置插入图标，`key` 支持`icons.yml`中配置好的图标，也可支持外链图标

## 跟随文本

icon后可以跟随文本，设置文本后将独立为行元素
{% icon default:goback 返回 %}{% icon default:goback %}

{% folding child:codeblock open:false color:default 查看代码 %}

```markdown
{% icon default:goback 返回 %}{% icon default:goback %}
```

{% endfolding %}
上边两个图标即使写在同一行，第一个也会单独为行元素

## 使用外链图标

{% icon https://api.iconify.design/fluent-emoji-flat/alarm-clock.svg %}
{% icon https://api.iconify.design/noto-v1/christmas-tree.svg %}
{% icon https://api.iconify.design/noto-v1/camel.svg %}

{% folding child:codeblock open:false color:default 查看代码 %}

```markdown
{% icon https://api.iconify.design/fluent-emoji-flat/alarm-clock.svg %}
{% icon https://api.iconify.design/noto-v1/christmas-tree.svg %}
{% icon https://api.iconify.design/noto-v1/camel.svg %}
```

{% endfolding %}

### icon外链网站

{% link https://iconify.design/ desc:true %}

## 指定图标颜色

{% icon default:goback color:blue %}
{% icon default:leftbar color:blue %}
{% icon default:rightbar color:blue %}
{% folding child:codeblock open:false color:default 查看代码 %}

```markdown 
{% icon default:goback color:blue %}
{% icon default:leftbar color:blue %}
{% icon default:rightbar color:blue %}
```

{% endfolding %}

添加`color:blue`指定图标颜色

### 修改默认图标颜色

```yml _config.stellar.yml
tag_plugins:
  icon:
    # 留空时，图标和文字颜色相同
    default_color: accent # theme, accent, red, orange, yellow, green, cyan, blue, purple
```

## 自定义样式

{% icon https://api.iconify.design/mdi/access-point.svg?color=red style:height:80px;width:80px %}
{% folding child:codeblock open:false color:default 查看代码 %}

```markdown 
{% icon https://api.iconify.design/mdi/access-point.svg?color=red style:height:80px;width:80px %}
```

{% endfolding %}

通过指定`style`属性，可以自定义图标样式，{% mark color:yellow 只对外链图标生效 %}，`style`参数中间{% mark color:yellow
不能有空格 %}

## 属性

| 属性名   | 说明                           |
|-------|------------------------------|
| key   | 在icons.yml中配置的图标key，或者外链图标地址 |
| text  | icon跟随文本                     |
| color | 图标颜色                         |
| style | 自定义图标样式                      |
