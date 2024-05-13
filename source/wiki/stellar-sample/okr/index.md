---
layout: wiki
wiki: stellar-sample
title: okr目标管理
---

## 基础用法

{% okr o1 %}

2024年的小目标：完成 Volantis 6.0 并发布上线
来自2025年的复盘：已《基本》实现目标 {% emoji tieba 滑稽 %}

<!-- okr kr1 percent:1-->

重构 tag-plugins 和 wiki 系统

- 当 {% mark KR %} 进度为 100% 时，标签默认显示为 {% mark color:green 已完成 %}
- 当 {% mark KR %} 未设置进度时，默认为 {% mark 0% %}
- 当 {% mark O %} 未设置进度时，则显示所有 {% mark KR %} 进度平均值

<!-- okr kr2 percent:0.9 status:off_track -->
完成主要页面设计稿
{% tabs align:left %}
<!-- tab 小提示1 -->
您可以在 _config.yml 文件中修改标签的颜色和文案
<!-- tab 小提示2 -->
您可以在 _config.yml 文件中增加任意的标签配置
{% endtabs %}

<!-- okr kr3 percent:-0.12 status:unfinished -->
完成前置准备工作（如果你知道答案，请在留言区帮帮我！🥹）
{% checkbox 在咸水和海滩之间找一亩地 %}
{% checkbox 求出圆周率后15位 %}
{% checkbox 找出宇宙的终极逻辑 %}
{% checkbox 去地狱里走两步 %}

<!-- okr kr-4 status:at_risk -->
开发、测试和发布
{% image /assets/logo.png height:64px 支持嵌套插入图片等其它简单组件 %}

{% endokr %}

{% folding child:codeblock open:false color:default 查看代码 %}

```markdonw
{% okr o1 %}

2024年的小目标：完成 Volantis 6.0 并发布上线
来自2025年的复盘：已《基本》实现目标 {% emoji tieba 滑稽 %}

<!-- okr kr1 percent:1 -->

重构 tag-plugins 和 wiki 系统
- 当 {% mark KR %} 进度为 100% 时，标签默认显示为 {% mark color:green 已完成 %}
- 当 {% mark KR %} 未设置进度时，默认为 {% mark 0% %}
- 当 {% mark O %} 未设置进度时，则显示所有 {% mark KR %} 进度平均值

<!-- okr kr2 percent:0.9 status:off_track -->
完成主要页面设计稿
{% tabs align:left %}
<!-- tab 小提示1 -->
您可以在 _config.yml 文件中修改标签的颜色和文案
<!-- tab 小提示2 -->
您可以在 _config.yml 文件中增加任意的标签配置
{% endtabs %}

<!-- okr kr3 percent:-0.12 status:unfinished -->
完成前置准备工作（如果你知道答案，请在留言区帮帮我！🥹）
{% checkbox 在咸水和海滩之间找一亩地 %}
{% checkbox 求出圆周率后15位 %}
{% checkbox 找出宇宙的终极逻辑 %}
{% checkbox 去地狱里走两步 %}

<!-- okr kr-4 status:at_risk -->
开发、测试和发布
{% image /assets/logo.png height:64px 支持嵌套插入图片等其它简单组件 %}

{% endokr %}
```

{% endfolding %}

### 语法格式

```markdown
{% okr title [percent:0.5] [status:on_track] [color:green] %}


<!-- okr kr[index] percent:1 [status:]  -->
title
[note]
...

{% endokr %}
```

可以在 `okr` 标签中直接设置`percent`完整度，`status`状态，`color`整个okr组件的颜色。如果不设置，则根据所有kr项计算平均值显示。
子项的参数中必须要以`kr`开头。

`status`根据配置文件中的配置使用，可自行添加或修改
```yaml _config.stellar.yml
tag-plugins:
  okr:
  border: true # 是否显示边框
  status: # 可以自行增加
    # 进行中状态
    in_track:
      color: blue # red, orange, yellow, green, cyan, blue, purple
      label: 正常
    at_risk:
      color: yellow
      label: 风险
    off_track:
      color: orange
      label: 延期
    # 结果状态
    finished:
      color: green
      label: 已完成
    unfinished:
      color: red
      label: 未完成
```

`title`okr的标题，`note`内容将作为`markdown`渲染。

## 属性

### okr

| 属性      | 说明                                   |
|---------|--------------------------------------|
| title   | okr的标题                               |
| percent | okr的完整度，不填时为所有子项的平均值                 |
| status  | okr的状态，不填时根据percent值设置， >=1为完成，其余为正常 |
| color   | okr组件的颜色                             |

### okr 子项


| 属性      | 说明                                   |
|---------|--------------------------------------|
| title   | okr的标题                               |
| percent | okr的完整度，不填时为0                        |
| status  | okr的状态，不填时根据percent值设置， >=1为完成，其余为正常 |


