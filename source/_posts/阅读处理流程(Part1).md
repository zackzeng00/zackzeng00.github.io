---
title: 信息处理的流程（Part1）
date: 2022-01-05
tag:
  - 教程
  - cubox
- Inoreader
toc: true
---

## 主要工具
目前信息处理一共用到的工具主要包含[inoreader][1]，[cubox][2]，[obsidian][3]。

## 主要流程
### 收集
`inoreader` 主要用来收集主要的信息。

信息来源主要是三类：
1. 没有RSS源的信息来源。搭配[rsshub][4]来使用，可以将很多常用的网站的信息变成RSS订阅源。
2. 已经拥有rss来源的网站。比如[少数派][5]这类自己就有rss源的网站。
3. 微信公众号：有不少付费与免费服务，可以提供微信公众号转RSS，我用的付费的有：[今天看啥][6]  免费的有：[feeddd][7] 等等，可以自己找找。
信息的分类
1. 科技类：本身工作属性，关注互联网信息与动态
2. 游戏类：包含游戏资讯网站，毕竟现在假假也是一个游戏开发者。
3. 新闻：主要是海外的一些新闻网站。中文媒体居多，新闻也有，因为英语阅读的效率问题，Inoreader自带翻译功能也提升不少效率。也是订阅inoreader的主要原因。
4. 娱乐：这块就是大面积扫包含微博热榜，知乎热榜。

### 细读
 细读这部分，主要用到的[cubox][8]。
通过[ifttt][9]，加上`cubox`的API接口，生成了一个 星标inoreader文章自动导入cubox

Cubox的标注以及导出分享功能。非常不错。


[1]:	www.inoreader.com
[2]:	cubox.pro
[3]:	https://obsidian.md/
[4]:	https://docs.rsshub.app/
[5]:	www.sspai.com
[6]:	http://www.jintiankansha.me/
[7]:	feeddd.org
[8]:	cubox.pro
[9]:	ifttt.com