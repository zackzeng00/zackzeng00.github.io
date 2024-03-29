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
#### Cubox
他是一款稍后阅读App，之前一直用Pocket，但是对国内的支持比较一般，虽然订阅了Pocket，但是基于Cubox国内支持的原因，后迁移到了cubox

他吸引我的点在于
1. 国内特性支持良好：
	1. 他支持微信转发消息直接进入cubox收件箱
2. 标注力优秀
	1. 标注样式漂亮
	2. 操作比较简洁
3. 开发团队效率高
	1. 这个可能是国内团队的优点，迭代非常快。很多bug修复很及时，特性的支持也很到位。
4. 优秀的分享体验
	1. Pocket由于墙的原因。里面东西分享很难
	2. cubox支持很好的分享体验 甚至标注也可以一起分享


[1]:	https://www.inoreader.com
[2]:	https://cubox.pro/
[3]:	https://obsidian.md/
[4]:	https://docs.rsshub.app/
[5]:	https://www.sspai.com
[6]:	http://www.jintiankansha.me/
[7]:	https://feeddd.org/
[8]:	https://cubox.pro/
[9]:	https://ifttt.com/home