---
layout: wiki
wiki: stellar-sample
title: grid网格分区容器
---

## 基础用法

{% grid bg:box %}
<!-- cell -->
cell-1

<!-- cell -->
cell-2

{% endgrid %}

{% folding child:codeblock open:false color:default 查看代码 %}

```markdown 
{% grid bg:box %}
<!-- cell -->
cell-1

<!-- cell -->
cell-2

{% endgrid %}
```

{% endfolding %}

### 语法格式

```markdown 
{% grid [bg:box/card] [w:240px] [c:2] [gap:16px] [br:12px] %}

<!-- cell -->
left body

<!-- cell -->
right body

{% endgrid %}
```

### 设置列数

默认的布局为【最小宽度为240px】即如果页面宽度大于 480px 则会显示为 2 列，大于 720px 则会显示为 3 列，以此类推。
也可以通过 `c:` 属性来设置列数，例如：`c:3`

{% grid c:3 bg:box %}
<!-- cell -->
cell-1

<!-- cell -->
cell-2

<!-- cell -->
cell-3

{% endgrid %}

可以使用`w`参数修改最小宽度。

### 背景样式

不设置样式
{% grid c:3 %}
<!-- cell -->
cell-1

<!-- cell -->
cell-2

<!-- cell -->
cell-3
{% endgrid %}

普通box样式

{% grid bg:box c:3 %}
<!-- cell -->
cell-1

<!-- cell -->
cell-2

<!-- cell -->
cell-3
{% endgrid %}

卡片样式

{% grid bg:card c:3 %}
<!-- cell -->
cell-1

<!-- cell -->
cell-2

<!-- cell -->
cell-3

{% endgrid %}

### 设置间距

默认间距为16px，如果需要修改，可以使用`gap`属性，例如：`gap:24px`

{% grid bg:box c:3 gap:24px %}
<!-- cell -->
cell-1

<!-- cell -->
cell-2

<!-- cell -->
cell-3
{% endgrid %}

### 设置圆角

默认圆角为12px，如果需要修改，可以使用`br`属性，例如：`br:30px`

{% grid bg:box c:3 gap:24px br:30px %}
<!-- cell -->
cell-1

<!-- cell -->
cell-2

<!-- cell -->
cell-3
{% endgrid %}

## 属性

| 属性  | 说明              |
|-----|-----------------|
| bg  | 设置背景样式 box/card |
| br  | 设置圆角            |
| c   | 设置列数，不设置按照宽度自适应 |
| gap | 设置间距            |
| w   | 设置最小宽度          |
