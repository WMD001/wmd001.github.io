---
layout: wiki
wiki: stellar-sample
title: gallery图库容器
---

## 基础用法

`gallery`标签内部只能填写`md`格式的图片

{% gallery %}
![@tianhao_wang](https://images.unsplash.com/photo-1688142202243-e218ad203952?w=800&auto=format&fit=crop&q=60&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHx0b3BpYy1mZWVkfDYzfEZ6bzN6dU9ITjZ3fHxlbnwwfHx8fHw%3D)
![@eberhard](https://images.unsplash.com/photo-1700994630045-f7a20df6d92e?w=800&auto=format&fit=crop&q=60&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwcm9maWxlLXBhZ2V8MjN8fHxlbnwwfHx8fHw%3D)
![@eberhard](https://images.unsplash.com/photo-1533274221104-015a584a1005?w=800&auto=format&fit=crop&q=60&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHx0b3BpYy1mZWVkfDE4fGJvOGpRS1RhRTBZfHxlbnwwfHx8fHw%3D)
![@eberhard](https://images.unsplash.com/photo-1539604214100-ab860d9082e0?w=800&auto=format&fit=crop&q=60&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHx0b3BpYy1mZWVkfDIxfGJvOGpRS1RhRTBZfHxlbnwwfHx8fHw%3D)
![@eberhard](https://images.unsplash.com/photo-1698843848092-588f9c1bb0bd?w=800&auto=format&fit=crop&q=60&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwcm9maWxlLXBhZ2V8Mzh8fHxlbnwwfHx8fHw%3D)
![@vklemen](https://images.unsplash.com/photo-1516571748831-5d81767b788d?q=80&w=2574&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D)
{% endgallery %}

{% folding child:codeblock open:false color:default 查看代码 %}

```markdown 
{% gallery %}
![@tianhao_wang](https://images.unsplash.com/photo-1688142202243-e218ad203952?w=800&auto=format&fit=crop&q=60&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHx0b3BpYy1mZWVkfDYzfEZ6bzN6dU9ITjZ3fHxlbnwwfHx8fHw%3D)
![@eberhard](https://images.unsplash.com/photo-1700994630045-f7a20df6d92e?w=800&auto=format&fit=crop&q=60&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwcm9maWxlLXBhZ2V8MjN8fHxlbnwwfHx8fHw%3D)
![@eberhard](https://images.unsplash.com/photo-1533274221104-015a584a1005?w=800&auto=format&fit=crop&q=60&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHx0b3BpYy1mZWVkfDE4fGJvOGpRS1RhRTBZfHxlbnwwfHx8fHw%3D)
![@eberhard](https://images.unsplash.com/photo-1539604214100-ab860d9082e0?w=800&auto=format&fit=crop&q=60&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHx0b3BpYy1mZWVkfDIxfGJvOGpRS1RhRTBZfHxlbnwwfHx8fHw%3D)
![@eberhard](https://images.unsplash.com/photo-1698843848092-588f9c1bb0bd?w=800&auto=format&fit=crop&q=60&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwcm9maWxlLXBhZ2V8Mzh8fHxlbnwwfHx8fHw%3D)
![@vklemen](https://images.unsplash.com/photo-1516571748831-5d81767b788d?q=80&w=2574&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D)
{% endgallery %}
```

{% endfolding %}

### 语法格式

```markdown 
{% gallery [layout:grid/flow] [size:mix/s/m/l/xl] [ratio:origin/square] %}
![title](/xxx.png)
![title](/xxx.png)
![title](/xxx.png)
![title](/xxx.png)
{% endgallery %}
```

### 设置布局

可以通过 `layout` 字段设置图片的布局方式，默认为 `grid`，可选值有：`grid/flow`，
使用 `grid` 为网格布局，可以使用size 字段设置图片大小，默认为 `mix`，可选值有：`mix/s/m/l/xl`，`ratio`
字段设置图片的宽高比，默认为 `origin`，可选值有：`origin/square`
使用 `flow` 为瀑布流布局

## 属性

| 属性     | 说明             |
|--------|----------------|
| layout | 布局方式 grid/flow |
| size   | 设置大小           |
| ratio  | 设置宽高比          |

