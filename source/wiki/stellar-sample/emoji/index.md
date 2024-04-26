---
layout: wiki
wiki: stellar-sample
title: emoji表情
---

## 基础用法

{% emoji 爱你 %}
{% emoji blobcat ablobcatattentionreverse %}
{% emoji tieba 滑稽 %}

{% folding child:codeblock open:false color:default 查看代码 %}

```markdown 
{% emoji 爱你 %}
{% emoji blobcat ablobcatattentionreverse %}
{% emoji tieba 滑稽 %}
```

{% endfolding %}

### 语法格式

```markdown 
{% emoji source name [height:20px] %}
```

内置了可配置的表情标签，`source`指定表情包来源，`name`指定表情名称。默认使用配置文件中`tag_plugins.emoji.default`配置的默认表情包。

## 指定高度

{% emoji height:30px 得意 %}
{% emoji height:40px 得意 %}
{% emoji height:50px 得意 %}

{% folding child:codeblock open:false color:default 查看代码 %}

```markdown 
{% emoji height:30px 得意 %}
{% emoji height:40px 得意 %}
{% emoji height:50px 得意 %}
```

{% endfolding %}

## 引入表情包

```yaml _config.stellar.yml 

tag_plugins:
  emoji:
    default: https://gcore.jsdelivr.net/gh/cdn-x/emoji/qq/${name}.gif
    twemoji: https://gcore.jsdelivr.net/gh/twitter/twemoji/assets/svg/${name}.svg
    qq: https://gcore.jsdelivr.net/gh/cdn-x/emoji/qq/${name}.gif
    aru: https://gcore.jsdelivr.net/gh/cdn-x/emoji/aru-l/${name}.gif
    tieba: https://gcore.jsdelivr.net/gh/cdn-x/emoji/tieba/${name}.png
    blobcat: https://gcore.jsdelivr.net/gh/norevi/waline-blobcatemojis@1.0/blobs/${name}.png
```

{% mark color:yellow 在配置文件中，文件名用`{name}`代替 %}

## 属性

| 属性名    | 说明    |
|--------|-------|
| source | 表情包来源 |
| name   | 表情包名称 |
| height | 高度    |

## QQ 表情速查

| 表情              | 索引  | 表情              | 索引 | 表情             | 索引 | 表情              | 索引  | 表情              | 索引  |
|-----------------|-----|-----------------|----|----------------|----|-----------------|-----|-----------------|-----|
| {% emoji 得意 %}  | 得意  | {% emoji 流泪 %}  | 流泪 | {% emoji 睡 %}  | 睡  | {% emoji 大哭 %}  | 大哭  | {% emoji 尴尬 %}  | 尴尬  |
| {% emoji 调皮 %}  | 调皮  | {% emoji 微笑 %}  | 微笑 | {% emoji 酷 %}  | 酷  | {% emoji 可爱 %}  | 可爱  | {% emoji 傲慢 %}  | 傲慢  |
| {% emoji 饥饿 %}  | 饥饿  | {% emoji 困 %}   | 困  | {% emoji 惊恐 %} | 惊恐 | {% emoji 流汗 %}  | 流汗  | {% emoji 憨笑 %}  | 憨笑  |
| {% emoji 奋斗 %}  | 奋斗  | {% emoji 疑问 %}  | 疑问 | {% emoji 嘘 %}  | 嘘  | {% emoji 晕 %}   | 晕   | {% emoji 敲打 %}  | 敲打  |
| {% emoji 再见 %}  | 再见  | {% emoji 发抖 %}  | 发抖 | {% emoji 爱情 %} | 爱情 | {% emoji 跳跳 %}  | 跳跳  | {% emoji 拥抱 %}  | 拥抱  |
| {% emoji 蛋糕 %}  | 蛋糕  | {% emoji 咖啡 %}  | 咖啡 | {% emoji 玫瑰 %} | 玫瑰 | {% emoji 太阳 %}  | 太阳  | {% emoji 握手 %}  | 握手  |
| {% emoji 胜利 %}  | 胜利  | {% emoji 飞吻 %}  | 飞吻 | {% emoji 西瓜 %} | 西瓜 | {% emoji 冷汗 %}  | 冷汗  | {% emoji 擦汗 %}  | 擦汗  |
| {% emoji 抠鼻 %}  | 抠鼻  | {% emoji 鼓掌 %}  | 鼓掌 | {% emoji 坏笑 %} | 坏笑 | {% emoji 左哼哼 %} | 左哼哼 | {% emoji 右哼哼 %} | 右哼哼 |
| {% emoji 哈欠 %}  | 哈欠  | {% emoji 委屈 %}  | 委屈 | {% emoji 可怜 %} | 可怜 | {% emoji 抱拳 %}  | 抱拳  | {% emoji 拳头 %}  | 拳头  |
| {% emoji 爱你 %}  | 爱你  | {% emoji NO %}  | NO | {% emoji OK %} | OK | {% emoji 转圈 %}  | 转圈  | {% emoji 喝彩 %}  | 喝彩  |
| {% emoji 棒棒糖 %} | 棒棒糖 | {% emoji 咖啡  %} | 咖啡 | {% emoji 可爱 %} | 可爱 | {% emoji 玫瑰 %}  | 玫瑰  | {% emoji 西瓜 %}  | 西瓜  |
| {% emoji 啤酒 %}  | 啤酒  | {% emoji 拳头 %}  | 拳头 | {% emoji 鼓掌 %} | 鼓掌 | {% emoji 礼物 %}  | 礼物  | {% emoji 呲牙 %}  | 呲牙  |
| {% emoji 激动 %}  | 激动  | {% emoji 飞吻 %}  | 飞吻 | {% emoji 亲亲 %} | 亲亲 | {% emoji 大哭 %}  | 大哭  |

## BlobCat 表情速查

| 表情                                           | 索引                       | 表情                                      | 索引                  |
|----------------------------------------------|--------------------------|-----------------------------------------|---------------------|
| {% emoji blobcat ablobcatheart %}            | ablobcatheart            | {% emoji blobcat ablobcatheartbroken %} | ablobcatheartbroken |
| {% emoji blobcat blobcatheart %}             | blobcatheart             | {% emoji blobcat blobcatheartpride %}   | blobcatheartpride   |
| {% emoji blobcat blobcatlove %}              | blobcatlove              | {% emoji blobcat blobcatkissheart %}    | blobcatkissheart    |
| {% emoji blobcat blobcatsnuggle %}           | blobcatsnuggle           | {% emoji blobcat comfyuee %}            | comfyuee            |
| {% emoji blobcat comfyslep %}                | comfyslep                | {% emoji blobcat blobcatcomfysweat %}   | blobcatcomfysweat   | 
| {% emoji blobcat blobcatcomftears %}         | blobcatcomftears         | {% emoji blobcat blobcatfacepalm %}     | blobcatfacepalm     |
| {% emoji blobcat blobcat0_0 %}               | blobcat0_0               | {% emoji blobcat blobcatangry %}        | blobcatangry        |
| {% emoji blobcat blobbanhammerr %}           | blobbanhammerr           | {% emoji blobcat blobcatt %}            | blobcatt            |
| {% emoji blobcat blobcatblush %}             | blobcatblush             | {% emoji blobcat blobcatcoffee %}       | blobcatcoffee       |
| {% emoji blobcat blobcatcry %}               | blobcatcry               | {% emoji blobcat blobcatdead %}         | blobcatdead         |
| {% emoji blobcat blobcatdied %}              | blobcatdied              | {% emoji blobcat blobcatdisturbed %}    | blobcatdisturbed    |
| {% emoji blobcat blobcatfearful %}           | blobcatfearful           | {% emoji blobcat blobcatfingerguns %}   | blobcatfingerguns   |
| {% emoji blobcat blobcatflip %}              | blobcatflip              | {% emoji blobcat blobcatflower %}       | blobcatflower       |
| {% emoji blobcat blobcatgay %}               | blobcatgay               | {% emoji blobcat blobcatgooglycry %}    | blobcatgooglycry    |
| {% emoji blobcat blobcatneutral %}           | blobcatneutral           | {% emoji blobcat blobcatopenmouth %}    | blobcatopenmouth    |
| {% emoji blobcat blobcatsadreach %}          | blobcatsadreach          | {% emoji blobcat blobcatscared %}       | blobcatscared       |
| {% emoji blobcat blobcatnomblobcat %}        | blobcatnomblobcat        | {% emoji blobcat blobcatpresentred %}   | blobcatpresentred   |
| {% emoji blobcat blobcatread %}              | blobcatread              | {% emoji blobcat blobcatsipsweat %}     | blobcatsipsweat     |
| {% emoji blobcat blobcatsnapped %}           | blobcatsnapped           | {% emoji blobcat blobcatthink %}        | blobcatthink        |
| {% emoji blobcat blobcattriumph %}           | blobcattriumph           | {% emoji blobcat blobcatumm %}          | blobcatumm          |
| {% emoji blobcat blobcatverified %}          | blobcatverified          | {% emoji blobcat blobcatbox %}          | blobcatbox          |
| {% emoji blobcat blobcatcaged %}             | blobcatcaged             | {% emoji blobcat blobcatgooglytrash %}  | blobcatgooglytrash  |
| {% emoji blobcat blobcatheadphones %}        | blobcatheadphones        | {% emoji blobcat blobcathighfive %}     | blobcathighfive     |
| {% emoji blobcat blobcatmelt %}              | blobcatmelt              | {% emoji blobcat blobcatmeltthumb %}    | blobcatmeltthumb    |
| {% emoji blobcat blobcatnotlikethis %}       | blobcatnotlikethis       | {% emoji blobcat blobcatsaitama %}      | blobcatsaitama      |
| {% emoji blobcat blobcatyandere %}           | blobcatyandere           | {% emoji blobcat blobcatpeek2 %}        | blobcatpeek2        |
| {% emoji blobcat blobcatpeekaboo %}          | blobcatpeekaboo          | {% emoji blobcat blobcatphoto %}        | blobcatphoto        |
| {% emoji blobcat ablobcatattentionreverse %} | ablobcatattentionreverse | {% emoji blobcat ablobcatreachrev %}    | ablobcatreachrev    |
| {% emoji blobcat ablobcatwave %}             | ablobcatwave             | {% emoji blobcat blobcatalt %}          | blobcatalt          |
| {% emoji blobcat blobcatpolice %}            | blobcatpolice            | {% emoji blobcat blobcatshocked %}      | blobcatshocked      |
| {% emoji blobcat ablobcatrainbow %}          | ablobcatrainbow          |                                         |                     |
