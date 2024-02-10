---
layout: wiki
wiki: stellar-sample
title: 组件总览
---

{% quot 表达类标签 %}

{% grid bg:block %}
<!-- cell -->
[emoji表情](emoji)

{% box color:blue %}

{% emoji 爱你 %} {% emoji blobcat ablobcatrainbow %} {% emoji blobcat ablobcatattentionreverse %} {% emoji tieba 滑稽 %}

{% endbox %}

<!-- cell -->
[Mark行内文本标记](mark)

{% box %}

{% mark 默认 %} {% mark 红 color:red %} {% mark 橙 color:orange %} {% mark 黄 color:yellow %} {% mark 绿 color:green %} 

{% endbox %}

{% endgrid %}


{% grid bg:block %}

<!-- cell  -->
[hashtag标签]()

{% box color:blue %}

{% hashtag Stellar https://xaoxuu.com/wiki/stellar/ %}
{% hashtag Hexo https://hexo.io/ %}
{% hashtag GitHub https://github.com/xaoxuu/ %}
{% hashtag Gitea https://git.xaox.cc/ color:green %}

{% endbox %}

<!-- cell  -->
[image图片标签]()

{% box color:blue %}



{% endbox %}

{% endgrid %}


{% grid bg:block %}

<!-- cell  -->

[quot引用]()

{% box color:blue %}

{% quot 个人博客 %}

{% endbox %}

<!-- cell  -->

[poetry诗词]()

{% box color:blue %}

{% poetry 游山西村 author:陆游 footer:诗词节选 %}
莫笑农家腊酒浑，丰年留客足鸡豚。
**山重水复疑无路，柳暗花明又一村。**
箫鼓追随春社近，衣冠简朴古风存。
从今若许闲乘月，拄杖无时夜叩门。
{% endpoetry %}

{% endbox %}

{% endgrid %}

{% grid bg:block %}

<!-- cell  -->

[note备注块]()

{% note 标题 这是一段备注块 %}

{% note color:blue 标题 这是一段彩色的备注块 %}

<!-- cell  -->

[link链接标签]()

{% link https://xaoxuu.com/blog/20221029/ desc:true %}

{% endgrid %}

{% box %}

[OKR目标管理]()

{% okr o1 %}

2024年目标，学习一门新语言，完成一个项目

<!-- okr kr1 percent:0.2 status:unfinished -->
学习go语言
- 基本语法

<!-- okr kr2 percent:0.1 status:unfinished -->
Wx_Msg_Notify，windows平台上微信消息通知工具
- python版开发
- 界面丰富

{% endokr %}

{% endbox %}

{% box %}

[copy复制行]()

{% copy git:https prefix:$ wmd001.com/wmd001.github.io  %}
{% copy wmd001.com/wmd001.github.io prefix:$ %}

{% endbox %}

{% grid bg:block %}

<!-- cell  -->

[radio单选]()

{% radio 未选择 %}
{% radio checked:true 已选择 %}

<!-- cell  -->

[checkbox复选]()

{% checkbox 普通的没有勾选的复选框 %}
{% checkbox checked:true 普通的已勾选的复选框 %}
{% checkbox symbol:plus color:green checked:true 显示为加号的绿色的已勾选的复选框 %}
{% checkbox symbol:minus color:yellow checked:true 显示为减号的黄色的已勾选的复选框 %}
{% checkbox symbol:times color:red checked:true 显示为乘号的红色的已勾选的复选框 %}

{% endgrid %}

{% grid bg:block %}

<!-- cell  -->

[navbar导航栏]()

{% navbar active:/wiki/ [文章](/) [项目](/wiki/) [留言](#comments) [GitHub](https://github.com/xaoxuu/) %}


<!-- cell  -->

[文本修饰标签集]()

- 这是 {% psw 密码 %} 标签
- 这是 {% u 下划线 %} 标签
- 这是 {% emp 着重号 %} 标签
- 这是 {% wavy 波浪线 %} 标签
- 这是 {% del 删除线 %} 标签
- 这是 {% sup 上角标 color:red %} 标签
- 这是 {% sub 下角标 %} 标签
- 这是 {% kbd 键盘样式 %} 标签，试一试：{% kbd ⌘ %} + {% kbd D %}

{% endgrid %}

{% box %}

[frame设备框架]()
{% frame iphone11 img:/assets/wiki/prohud/toast/demo-loading.png video:/assets/wiki/prohud/toast/demo-loading.mp4 focus:top %}

{% endbox %}

{% quot 数据集合类标签 %}

{% quot 容器类标签 %}

{% quot 表达类标签 %}