---
title: 设置giscus主题字体
tags: [giscus, giscus主题字体]
categories: [杂记]
poster:
  topic: 标题上方的小字
  headline: 大标题
  caption: 标题下方的小字
  color: 标题颜色
date: 2024-04-25 14:07:26
description:
---

## 原因

博客使用了雾霭文楷，但是giscus的评论框字体和博客不匹配，导致评论和文章显示不协调。

## 做法

创建一个css文件。内容如下：

```css
/*引入giscus preferred_color_scheme 主题文件*/
@import url("//giscus.app/themes/preferred_color_scheme.css");
/*引入字体*/
@import url("//npm.elemecdn.com/lxgw-wenkai-screen-webfont/style.css");

/*设置评论区字体*/
body {
    font-family: LXGW WenKai Screen,-apple-system,BlinkMacSystemFont,Segoe UI,Helvetica,Arial,sans-serif,Apple Color Emoji,Segoe UI Emoji;
}
```

之后在giscus的设置中，需要将css的文件地址填入。
我的做法是将css文件上传到github，然后使用github的raw地址。

{% copy https://raw.githack.com/WMD001/giscus-theme-font/main/lxgw-wenkai.css %}

{% note color:default 注意 直接使用raw文件的地址是不行的，不能自动执行css，可以把`githubusercontent`替换成`githack` %}

{% mark 如果有自己的服务器，也可以放在自己的服务器上 color:yellow %}