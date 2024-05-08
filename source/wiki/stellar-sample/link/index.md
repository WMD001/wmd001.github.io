---
layout: wiki
wiki: stellar-sample
title: link链接标签
---

## 基础用法

{% link https://wmd001.top 个人网站 desc:true icon:/assets/avatar.png %}
{% link https://wmd001.top/blog/20240404/ desc:true icon:/assets/favicon.png %}

{% folding child:codeblock open:false color:default 查看代码 %}

```markdown
{% link https://wmd001.top 个人网站 desc:true icon:/assets/avatar.png %}
{% link https://wmd001.top/blog/20240404/ desc:true icon:/assets/favicon.png %}
```

{% endfolding %}


### 语法格式

{% link href [title] [desc:bool] [icon:src] %}


## 自动抓取

参考一下项目进行自部署，并配置接口地址api
{% link https://github.com/xaoxuu/site-info-api %}

```yaml _config.stellar.yml
tag_plugins:
  # {% link %}
  linkcard:
    # 设置 api 可以自动提取网页标题、图标，服务部署方法：https://github.com/xaoxuu/site-info-api/
    # 接口测试通过后，把按钮的 href 部分替换成 ${href} 之后填写到下方，例如：https://api.vlts.cc/site_info/v1?url=${href}
    api: 
```

## 属性

| 属性名   | 说明                      |
|-------|-------------------------|
| href  | 链接地址                    |
| title | 手动设置标题（为空时会自动抓取页面标题）    |
| desc  | 手动设置图标（为空时会自动抓取页面图标）    |
| icon  | 是否显示摘要描述，为true时将会显示页面描述 |
