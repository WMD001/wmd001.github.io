---
layout: wiki
wiki: stellar-sample
title: 文本修饰标签集
---

{% quot icon:hashtag el:h2 效果示例 %}

{% grid c:2 %}

<!-- cell -->
{% quot icon:hashtag el:h5 密码 %}

{% tabs align:center %}

<!-- tab 效果 -->
这是 {% psw 密码 %} 标签

<!-- tab 代码 -->
```
这是 {% psw 密码 %} 标签
```
{% endtabs %}

<!-- cell -->
{% quot icon:hashtag el:h5 下划线 %}

{% tabs align:center %}

<!-- tab 效果 -->
这是{% u 下划线 %}标签

<!-- tab 代码 -->
```
这是{% u 下划线 %}标签
```
{% endtabs %}

<!-- cell -->
{% quot icon:hashtag el:h5 着重号 %}

{% tabs align:center %}

<!-- tab 效果 -->
这是 {% emp 着重号 %} 标签

<!-- tab 代码 -->
```
这是 {% emp 着重号 %} 标签
```
{% endtabs %}

<!-- cell -->
{% quot icon:hashtag el:h5 波浪线 %}

{% tabs align:center %}

<!-- tab 效果 -->
这是 {% wavy 波浪线 %} 标签

<!-- tab 代码 -->
```
这是 {% wavy 波浪线 %} 标签
```
{% endtabs %}

<!-- cell -->
{% quot icon:hashtag el:h5 上角标 %}

{% tabs align:center %}

<!-- tab 效果 -->
这是{% sup 上角标 %}标签

<!-- tab 代码 -->
```
这是{% sup 上角标 %}标签
```
{% endtabs %}

<!-- cell -->
{% quot icon:hashtag el:h5 下角标 %}

{% tabs align:center %}

<!-- tab 效果 -->
这是 {% sub 下角标 %} 标签

<!-- tab 代码 -->
```
这是 {% sub 下角标 %} 标签
```
{% endtabs %}

<!-- cell -->
{% quot icon:hashtag el:h5 删除线 %}

{% tabs align:center %}

<!-- tab 效果 -->
这是 {% del 删除线 %} 标签

<!-- tab 代码 -->
```
这是 {% del 删除线 %} 标签
```
{% endtabs %}

<!-- cell -->
{% quot icon:hashtag el:h5 键盘样式 %}

{% tabs align:center %}

<!-- tab 效果 -->
这是 {% kbd 键盘样式%} 标签

<!-- tab 代码 -->
```
这是 {% kbd 键盘央视 %} 标签，试一试：{% kbd ctrl %} +：{% kbd c %} 
```
{% endtabs %}

{% endgrid %}

{% note 上角标和小角标还可以设置color属性，<code>color:red</code>，效果如下：  %}

这是带颜色的 {% sup color:red 上角标 %} 和 {% sub color:red 下角标 %} 标签
