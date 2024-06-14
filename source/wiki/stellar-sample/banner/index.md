---
layout: wiki
wiki: stellar-sample
title: banner横幅容器
---

## 基础用法

### 语法格式

```markdown 
{% banner title [subtitle] [bg:src] [avatar:src] [link] %}
{% navbar xxx %}
{% endbanner %}
```

### 用于独立页面顶部

{% banner 随记 bg:/assets/banner.jpg %}
{% navbar active:/notes/ [随记](/notes/) [收藏](/bookmark/) %}
{% endbanner %}

### 用于用户个人资料页

{% banner 某某 这是个人简介 avatar:/assets/avatar.png bg:/assets/banner.jpg %}
{% endbanner %}

### 用作文章摘要卡片

设置 `link` 可以让整个卡片响应点击事件，实现点击跳转到对应文章。
{% banner 博客进阶：自动化部署 本文讲了如何利用脚本和 GitHub Actions 简化博客搭建和部署流程，提高效率。 bg:
/assets/xaoxuu/blog/2022-1126a@2x.jpg link:/blog/20221126/ %}
{% endbanner %}

## 属性

| 属性       | 说明   |
|----------|------|
| title    | 标题   |
| subtitle | 副标题  |
| bg       | 背景   |
| avatar   | 头像   |
| link     | 跳转地址 |

