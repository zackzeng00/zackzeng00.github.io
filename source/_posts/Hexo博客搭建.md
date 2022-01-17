
---
title:  如何用Hexo搭建个人Blog
date:2022-01-17
tags: 
    - 转载
    - hexo
    - 教程
toc:true 
---

>> 一直想写一个介绍搭建的blog 但是有很多不错的，所以也就偷懒了。转载一片
>> [转载来源](https://qiutedyuan.github.io/blog/2019/06/01/%E5%A6%82%E4%BD%95%E7%94%A8Hexo%E6%90%AD%E5%BB%BA%E4%B8%AA%E4%BA%BABlog/)
# 如何用Hexo搭建个人Blog

[qiutedyuan.github.io](https://qiutedyuan.github.io/blog/2019/06/01/%E5%A6%82%E4%BD%95%E7%94%A8Hexo%E6%90%AD%E5%BB%BA%E4%B8%AA%E4%BA%BABlog/)

最近对原有的[个人主页](https://qiutedyuan.github.io/)重构时觉得生写Html网页太费力，且无法轻易拓展。故学习了一下[Hexo](https://hexo.io/zh-cn/docs/index.html)这个由md文件方便地渲染出Html文本的工具。开发过程中遇到了一些阻碍，总结一下心得。整个搭建过程主要是依赖一篇非常详细的[教程](https://godweiyang.com/2018/04/13/hexo-blog/)。不过由于具体需求有一定出入，这边从零开始总结一个完整的流程。如有因版本更新而不适用的部分，请联系我，会做出调整。

## 使用Github Pages

[Github](https://github.com/)账号的申请不赘述了。开启[Github Pages](https://pages.github.com/)，只需要新建一个以`<username>.github.io`为名的repository，private亦可。-
![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fqiutedyuan.github.io%2Fblog%2F2019%2F06%2F01%2F%25E5%25A6%2582%25E4%25BD%2595%25E7%2594%25A8Hexo%25E6%2590%25AD%25E5%25BB%25BA%25E4%25B8%25AA%25E4%25BA%25BABlog%2Frepo.png)-
之后，在`Settings`中找到Github Pages的选项：-
![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fqiutedyuan.github.io%2Fblog%2F2019%2F06%2F01%2F%25E5%25A6%2582%25E4%25BD%2595%25E7%2594%25A8Hexo%25E6%2590%25AD%25E5%25BB%25BA%25E4%25B8%25AA%25E4%25BA%25BABlog%2Fgh-pages.png)-
打开对应开关并选择主题即可。注意：空的Repo不存在master branch，无法开启Github Pages，至少需要加入一个文件（如`README.md`）。

## <username>.github.io 已被占用

如果默认的链接已经存在[个人主页](https://qiutedyuan.github.io/)了，可以另起一个任意名称的Repo（这里以`test`为例）。-
![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fqiutedyuan.github.io%2Fblog%2F2019%2F06%2F01%2F%25E5%25A6%2582%25E4%25BD%2595%25E7%2594%25A8Hexo%25E6%2590%25AD%25E5%25BB%25BA%25E4%25B8%25AA%25E4%25BA%25BABlog%2Ftest.png)-
此时Pages则会自动被放到`<username>.github.io/test/`域名下。-
![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fqiutedyuan.github.io%2Fblog%2F2019%2F06%2F01%2F%25E5%25A6%2582%25E4%25BD%2595%25E7%2594%25A8Hexo%25E6%2590%25AD%25E5%25BB%25BA%25E4%25B8%25AA%25E4%25BA%25BABlog%2Ftest-pages.png)-
选择主题后，可以很快捷地生成一个pages页面。-
![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fqiutedyuan.github.io%2Fblog%2F2019%2F06%2F01%2F%25E5%25A6%2582%25E4%25BD%2595%25E7%2594%25A8Hexo%25E6%2590%25AD%25E5%25BB%25BA%25E4%25B8%25AA%25E4%25BA%25BABlog%2Ftest-first.png)

> Remarks：
> 
> *   可以在`test > environment`中查看编译情况。确定最新的commit已经编译完成后，若浏览器没有刷新，需要清理缓存，或者换用非常用浏览器查看。
> *   `<username>.github.io`的页面只能编译master branch，其他页面也可编译master下的`/docs`目录。但是多branch是不支持的。推荐Enforce HTTPS。

* * *

## 使用Hexo

本文操作系统为64位Windows 10教育版。

## 安装Git Bash

原来习惯用[Ubuntu on Windows](https://tutorials.ubuntu.com/tutorial/tutorial-ubuntu-on-windows)，但是过程中遇到了很多问题，因此还是推荐使用[Git Bash](https://gitforwindows.org/)，对于Windows的支持（如文件名、同步锁等）更友好。安装完成后左下角搜索即可打开Git Bash。MacOS上直接`brew install git`即可。

1-
2-

$ git --version-
git version 2.21.0.windows.1-

## 安装Node.js

最新版的Node.js请从[官网](https://nodejs.org/zh-cn/)下载。我使用的是原博主提供的v9.11.1版本[64位msi包](https://nodejs.org/dist/v9.11.1/node-v9.11.1-x64.msi)。安装过程简明。MacOS上直接`brew install node`即可。

1-
2-
3-
4-
5-

$ node \-v-
v9.11.1-
-
$ npm -v-
5.6.0-

## 安装Hexo

具体请依照[官网](https://hexo.io/zh-cn/docs/index.html)，完成前面的步骤后应该只需要`npm install -g hexo-cli`。会有一些报错，但可以无视。

1-
2-
3-
4-
5-
6-
7-

$ npm install -g hexo-cli-
<npm\-home>\\npm\\hexo \-> <npm\-home>\\npm\\node\_modules\\hexo-cli\\bin\\hexo-
npm WARN optional SKIPPING OPTIONAL DEPENDENCY: fsevents@1.2.9 (node\_modules\\hexo-cli\\node\_modules\\fsevents):-
npm WARN notsup SKIPPING OPTIONAL DEPENDENCY: Unsupported platform for fsevents@1.2.9: wanted {"os":"darwin","arch":"any"} (current: {"os":"win32","arch":"x64"})-
-
\+ hexo-cli@2.0.0-
updated 1 package in 1.819s-

1-
2-
3-
4-
5-
6-
7-
8-
9-
10-
11-
12-
13-
14-
15-
16-
17-

$ hexo -v-
hexo-cli: 2.0.0-
os: Windows\_NT 10.0.17134 win32 x64-
http\_parser: 2.8.0-
node: 9.11.1-
v8: 6.2.414.46\-node.23-
uv: 1.19.2-
zlib: 1.2.11-
ares: 1.13.0-
modules: 59-
nghttp2: 1.29.0-
napi: 3-
openssl: 1.0.2o-
icu: 61.1-
unicode: 10.0-
cldr: 33.0-
tz: 2018c-

## 初始化工作目录

这边以`D:\Documents\test`为例，在对应目录中执行`hexo init`。注意，目录必须为空，否则会报错

1-

<dir> not empty, please run \`hexo init\` on an empty folder and then copy your files into it-

> 原博客中先执行了`npm install hexo --save`，经测试这一步会由`hexo init`一并执行。

1-
2-
3-
4-
5-
6-
7-
8-
9-
10-
11-
12-
13-
14-
15-
16-
17-
18-
19-
20-
21-
22-
23-
24-

$ hexo init-
INFO Cloning hexo-starter https://github.com/hexojs/hexo-starter.git-
Cloning into 'D:\\Documents\\test'...-
remote: Enumerating objects: 6, done.-
remote: Counting objects: 100% (6/6), done.-
remote: Compressing objects: 100% (4/4), done.-
remote: Total 74 (delta 2), reused 4 (delta 2), pack-reused 68-
Unpacking objects: 100% (74/74), done.-
Submodule 'themes/landscape' (https://github.com/hexojs/hexo-theme-landscape.git) registered for path 'themes/landscape'-
Cloning into 'D:/Documents/test/themes/landscape'...-
remote: Enumerating objects: 1, done.-
remote: Counting objects: 100% (1/1), done.-
remote: Total 896 (delta 0), reused 0 (delta 0), pack-reused 895-
Receiving objects: 100% (896/896), 2.55 MiB | 1.06 MiB/s, done.-
Resolving deltas: 100% (479/479), done.-
Submodule path 'themes/landscape': checked out '73a23c51f8487cfcd7c6deec96ccc7543960d350'-
INFO Install dependencies-
npm WARN deprecated core-js@1.2.7: core-js@<2.6.8 is no longer maintained. Please, upgrade to core-js@3 or at least to actual version of core-js@2.-
npm notice created a lockfile as package\-lock.json. You should commit this file.-
npm WARN optional SKIPPING OPTIONAL DEPENDENCY: fsevents@1.2.9 (node\_modules\\fsevents):-
npm WARN notsup SKIPPING OPTIONAL DEPENDENCY: Unsupported platform for fsevents@1.2.9: wanted {"os":"darwin","arch":"any"} (current: {"os":"win32","arch":"x64"})-
-
added 420 packages in 24.517s-
INFO Start blogging with Hexo!-

1-
2-
3-

$ ls-
\_config.yml package.json scaffolds/ themes/-
node\_modules/ package-lock.json source/-

接着执行`npm install`，依照`package.json`安装依赖。

1-
2-
3-
4-
5-
6-
7-
8-
9-
10-
11-
12-
13-
14-
15-
16-
17-
18-
19-
20-
21-
22-
23-
24-
25-
26-

$ cat package.json-
{-
 "name": "hexo-site",-
 "version": "0.0.0",-
 "private": true,-
 "hexo": {-
 "version": ""-
 },-
 "dependencies": {-
 "hexo": "^3.8.0",-
 "hexo-generator-archive": "^0.1.5",-
 "hexo-generator-category": "^0.1.3",-
 "hexo-generator-index": "^0.2.1",-
 "hexo-generator-tag": "^0.2.0",-
 "hexo-renderer-ejs": "^0.3.1",-
 "hexo-renderer-stylus": "^0.3.3",-
 "hexo-renderer-marked": "^1.0.1",-
 "hexo-server": "^0.3.3"-
 }-
}-
-
$ npm install-
npm WARN optional SKIPPING OPTIONAL DEPENDENCY: fsevents@1.2.9 (node\_modules\\fsevents):-
npm WARN notsup SKIPPING OPTIONAL DEPENDENCY: Unsupported platform for fsevents@1.2.9: wanted {"os":"darwin","arch":"any"} (current: {"os":"win32","arch":"x64"})-
-
up to date in 8.202s-

## 预览网页

`hexo generate`/`hexo g`会将md文件编译为public下的html文本，`hexo server`/`hexo s`会将网页发布到`localhost:4000`。

1-
2-
3-
4-
5-
6-
7-
8-
9-
10-
11-
12-
13-
14-
15-
16-
17-
18-
19-
20-
21-
22-
23-
24-
25-
26-
27-
28-
29-
30-
31-
32-
33-
34-

$ hexo g && hexo s-
INFO Start processing-
INFO Files loaded in 188 ms-
INFO Generated: index.html-
INFO Generated: archives/index.html-
INFO Generated: fancybox/blank.gif-
INFO Generated: fancybox/jquery.fancybox.css-
INFO Generated: fancybox/jquery.fancybox.js-
INFO Generated: fancybox/jquery.fancybox.pack.js-
INFO Generated: fancybox/fancybox\_loading.gif-
INFO Generated: fancybox/fancybox\_overlay.png-
INFO Generated: fancybox/fancybox\_loading@2x.gif-
INFO Generated: fancybox/fancybox\_sprite.png-
INFO Generated: fancybox/fancybox\_sprite@2x.png-
INFO Generated: archives/2019/06/index.html-
INFO Generated: archives/2019/index.html-
INFO Generated: css/fonts/FontAwesome.otf-
INFO Generated: js/script.js-
INFO Generated: fancybox/helpers/jquery.fancybox-media.js-
INFO Generated: fancybox/helpers/jquery.fancybox-buttons.js-
INFO Generated: css/fonts/fontawesome-webfont.woff-
INFO Generated: css/style.css-
INFO Generated: fancybox/helpers/jquery.fancybox-buttons.css-
INFO Generated: fancybox/helpers/jquery.fancybox-thumbs.css-
INFO Generated: fancybox/helpers/jquery.fancybox-thumbs.js-
INFO Generated: fancybox/helpers/fancybox\_buttons.png-
INFO Generated: css/fonts/fontawesome-webfont.eot-
INFO Generated: css/fonts/fontawesome-webfont.svg-
INFO Generated: css/images/banner.jpg-
INFO Generated: css/fonts/fontawesome-webfont.ttf-
INFO Generated: 2019/06/02/hello-world/index.html-
INFO 28 files generated in 385 ms-
INFO Start processing-
INFO Hexo is running at http://localhost:4000 . Press Ctrl+C to stop.-

在浏览器中键入`localhost:4000`以预览网页。-
![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fqiutedyuan.github.io%2Fblog%2F2019%2F06%2F01%2F%25E5%25A6%2582%25E4%25BD%2595%25E7%2594%25A8Hexo%25E6%2590%25AD%25E5%25BB%25BA%25E4%25B8%25AA%25E4%25BA%25BABlog%2Fhexo-init.png)-
至此，本地Hexo的部署基本完成。按`Ctrl+C`以可以关闭部署。

> Remark：
> 
> *   如果4000端口被占用，部署时用`hexo s -p 5000`指定空闲的端口。

* * *

## 修改主题

这里使用[Bean Tech](http://beantech.org/)主题，先从[Github](https://github.com/YenYuHsuan/hexo-theme-beantech)上clone到本地。

1-
2-
3-
4-
5-
6-
7-
8-
9-

$ git clone https://github.com/YenYuHsuan/hexo-theme-beantech.git ./hexo-beantech-
Cloning into './hexo-beantech'...-
remote: Enumerating objects: 207, done.-
remote: Total 207 (delta 0), reused 0 (delta 0), pack-reused 207-
Receiving objects: 100% (207/207), 13.18 MiB | 1.31 MiB/s, done.-
Resolving deltas: 100% (64/64), done.-
-
$ ls hexo-beantech/-
\_config.yml LICENSE package.json README.md scaffolds/ source/ themes/-

这个主题需要覆盖原文件，执行`cp -r hexo-beantech/. ./`。再次执行`npm install`。-
现在可以再用`hexo clean && hexo g && hexo s`看一下效果。-
![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fqiutedyuan.github.io%2Fblog%2F2019%2F06%2F01%2F%25E5%25A6%2582%25E4%25BD%2595%25E7%2594%25A8Hexo%25E6%2590%25AD%25E5%25BB%25BA%25E4%25B8%25AA%25E4%25BA%25BABlog%2Fbean-tech.png)

> Remark:-
> 安装主题后Hexo警告`DeprecationWarning: fs.SyncWriteStream is deprecated.`-
> 根据网上的方案，分别执行以下命令升级解决。
> 
> 1-
> 2-
> 3-
> 4-
> 
> npm install hexo-fs \--save-
> npm install hexo-deployer-git@0.3.1 \--save-
> npm install hexo-renderer-ejs@0.3.1 \--save-
> npm install hexo-server@0.2.2 \--save-

* * *

## 个人配置

## 目录结构

1-
2-
3-
4-
5-
6-
7-
8-
9-
10-
11-
12-
13-

.-
├── \_config.yml // 全局设置-
├── package.json // npm依赖包-
├── public // 部署的网页-
├── scaffolds // 新建模板-
├── source // 编译public的源文件-
| ├── \_drafts-
| └── \_posts-
└── themes-
 └── beantech-
 ├── \_config.yml // 代码高亮设置-
 ├── sources-
 └── layout // html配置-

## Config文件配置

删除`./source/CNAME`，否则Github编译报错。

1-
2-
3-
4-
5-
6-
7-
8-
9-
10-
11-
12-
13-
14-
15-
16-
17-
18-
19-
20-
21-
22-
23-
24-
25-
26-
27-
28-
29-
30-
31-
32-
33-
34-
35-
36-
37-
38-
39-
40-
41-
42-
43-
44-
45-
46-
47-
48-
49-
50-
51-
52-
53-
54-
55-
56-
57-
58-
59-
60-
61-
62-
63-
64-
65-
66-
67-
68-
69-
70-
71-
72-
73-
74-
75-
76-
77-
78-
79-
80-
81-
82-
83-
84-
85-
86-
87-
88-
89-
90-
91-
92-
93-
94-
95-
96-
97-
98-
99-
100-
101-
102-
103-
104-
105-
106-
107-
108-
109-
110-
111-
112-
113-
114-
115-
116-
117-
118-
119-
120-
121-
122-
123-
124-
125-
126-
127-
128-
129-
130-
131-
132-
133-
134-
135-
136-
137-
138-
139-
140-
141-
142-
143-
144-
145-
146-
147-
148-
149-
150-
151-
152-
153-
154-
155-
156-
157-
158-
159-
160-
161-
162-
163-
164-
165-
166-
167-
168-
169-
170-
171-
172-
173-

\# Hexo Configuration-
\## Docs: https://hexo.io/docs/configuration.html-
\## Source: https://github.com/hexojs/hexo/-
-
\# Site-
title: Your Name // 标题，出现在左上角及首页居中-
subtitle: Personal Blog // 副标题，出现在标题下方-
author: Your Name // 作者，每一条Post署名及底部版权-
language: en\_US // 语言，见.themes/beantech/languages\_to\_be\_added-
timezone: Hongkong // 时区-
-
\# URL-
\## If your site is put in a subdirectory, set url as 'http://yoursite.com/child' and root as '/child/'-
url: https://<username>.github.io/test // 远程地址，这里以子目录为例-
root: /test/ // 在子目录的话需要修改-
permalink: :year/:month/:day/:title/-
permalink\_defaults:-
-
#Custom Setting Start-
-
\# Site settings-
SEOTitle: Your Name // 出现在标签栏-
email: <username>@gmail.com // 邮箱，不确定出现在哪里-
description: ""-
keyword: ""-
header-img: img/header\_img/xxx.png // 主页背景，对应地址./source/img/header\_img/...-
signature: true-
signature-img: img/signature/xxx.png // 签名，对应地址./source/img/signature/...-
-
\# SNS settings // 填写对应信息即可-
\# RSS: false-
\# weibo\_username: <username>-
\# zhihu\_username: <username>-
github\_username: <username>-
\# twitter\_username: <username>-
facebook\_username: <username>-
linkedin\_username: <username>-
-
\# Build settings-
anchorjs: true-
-
\# Disqus settings // 禁用Disqus评论-
\# disqus\_username: your-disqus-ID-
-
\# Duoshuo settings-
\# duoshuo\_username: kaijun-
\# Share component is depend on Comment so we can NOT use share only.-
\# duoshuo\_share: true // duoshuo评论也关掉-
-
\# Analytics settings-
\# Baidu Analytics-
\# ba\_track\_id: 4cc1f2d8f3067386cc5cdb626a202900-
\# Google Analytics-
\# ga\_track\_id: 'UA-XXXXXXXX-X' // 不知道怎么用，因此omment掉了-
\# ga\_domain: yoursite-
-
\# Sidebar settings-
sidebar: true-
sidebar-about-description: "Hi" // 简介，出现在右侧个人照片下方-
sidebar-avatar: img/xxx.png // 头像，对应地址./source/img/...-
widgets: // 边栏导航，我去掉了friends加入了archive-
\- featured-tags-
\- short-about-
\- recent-posts-
\# - friends-blog-
\- archive-
\# - category // category目前没有实现-
-
\# widget behavior-
\## Archive-
archive\_type: 'monthly'-
show\_count: true-
-
\## Featured Tags-
featured-tags: true-
featured-condition-size: 1 // 至少有2篇文章的tag会出现在feature中-
-
-
\## Friends // 全部comment掉，否则出现在post下方-
\# friends: \[-
\# {-
\# title: "Bean Tech",-
\# href: "http://beantech.org"-
\# },{-
\# title: "Kaijun's Blog",-
\# href: "http://blog.kaijun.rocks"-
\# },{-
\# title: "Hux Blog",-
\# href: "http://huangxuan.me"-
\# },{-
\# title: "It Helps SEO",-
\# href: "#"-
\# }-
\# \]-
-
#Custom Setting End-
-
\# Directory // 对应文件夹地址，不需要修改-
source\_dir: source-
public\_dir: public-
tag\_dir: tags-
archive\_dir: archives-
category\_dir: categories-
code\_dir: downloads/code-
i18n\_dir: :lang-
skip\_render:-
-
\# Writing // 默认新文件配置，不需要修改-
new\_post\_name: :title.md-
default\_layout: post-
titlecase: false-
external\_link: true-
filename\_case: 0-
render\_drafts: false-
post\_asset\_folder: true-
relative\_link: false-
future: true-
highlight:-
 enable: true-
 line\_number: true-
 auto\_detect: true-
 tab\_replace:-
-
\# Category & Tag-
default\_category: uncategorized-
category\_map:-
tag\_map:-
home\_posts\_tag: true // 是否在首页显示Tag-
-
\# Date / Time format-
\## Hexo uses Moment.js to parse and display date-
\## You can customize the date format as defined in-
\## http://momentjs.com/docs/#/displaying/format/-
date\_format: YYYY-MM-DD-
time\_format: HH:mm:ss-
-
\# Pagination-
\## Set per\_page to 0 to disable pagination-
per\_page: 10-
pagination\_dir: archives-
-
archive\_generator:-
 per\_page: 10-
 yearly: true-
 monthly: true-
 daily: false-
-
\# Markdown-it config-
\## Docs: https://github.com/celsomiranda/hexo-renderer-markdown-it/wiki-
markdown:-
 render:-
 html: true-
 xhtmlOut: false-
 breaks: true-
 linkify: true-
 typographer: true-
 quotes: '“”‘’'-
-
\# Extensions-
\## Plugins: https://hexo.io/plugins/-
\## Themes: https://hexo.io/themes/-
theme: beantech-
-
#sitemap-
sitemap:-
 path: sitemap.xml-
-
\# Deployment-
\## Docs: https://hexo.io/docs/deployment.html-
deploy:-
 type: git-
 repository: https://<repo>.git // 改成自己的Repository-
 branch:master // 只能编译master branch-

上述修改完成后，再次`hexo clean && hexo g && hexo s`，打开`localhost:4000`会自动跳转到`localhost:4000/test`。

## 其他配置

### 签名制作

Windows画图无法保存透明通道。使用画图3D画出来后，复制到ppt中，点选`格式>颜色>设置透明色`并点击背景，即可将背景设置为透明。（如果想做白色签名，就用黑色背景）。-
![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fqiutedyuan.github.io%2Fblog%2F2019%2F06%2F01%2F%25E5%25A6%2582%25E4%25BD%2595%25E7%2594%25A8Hexo%25E6%2590%25AD%25E5%25BB%25BA%25E4%25B8%25AA%25E4%25BA%25BABlog%2Fppt.png)-
完成后右键另存为图片，就保存了透明通道。

### 页面背景

主页的在`_config.yml`中已经配置过了。另外需要手动配置的页面是`./source/about/index.md`，`./source/archive/index.md`，`./source/tags/index.md`，`./source/404.md`。对应的图片放在`./source/img/header_img/...`。-
其中`description`不想要的话不能留空，这样会套用全局设置（跟首页相同）。要打一个空格`" "`。

### 文章模板

在`./scaffolds/`下，可以设置page和post的默认背景。`catalog`是目录的开关。

### 标签栏图标

位于`./themes/beantech/layout/_partial/head.ejs`第8行，对应图片存在`./source/img/...`。

### To Top 图标

在`./themes/beantech/source/css/rocket.styl`中有两个地方用到该图标，改为自己喜欢的即可，放在`./themes/beantech/source/css/images/...`

### 文中标题标记

原来是一个`B`，感觉比较丑。在`./themes/beantech/layout/post.ejs`的174行，我换成了`>`。

### 代码高亮

在`./themes/beantech/_config.yml`，我换成了`night eighties`。\\

* * *

## 修复 Bug

### Archive布局

Archive页面的布局不是很好，长的标题会越界。我的做法是把 `./themes/beantech/layout/archive.ejs`顶部的layout由`page`改为了`layout`，去掉sidebar。

### 目录问题

目录指向`#undefined`的bug是已知[issue](https://github.com/YenYuHsuan/hexo-theme-beantech/issues/11)。目前的解决方法是`./node_modules/hexo-toc/lib/filter.js`中，恢复第28行，comment第29-31行。但是会被npm install覆盖，仍然[open](https://github.com/huweihuang/hexo-theme-huweihuang/issues/5)。

### js文件找不到

`totop.js`，`toc.js`，以及`icon-wechat.png`找不到，是因为目录位置更改了。我的解决方法是在`./themes/beantech/layout/layout.ejs`中，comment掉`icon-wechat.png`的那一块，将另外两个js重定位如下。

1-
2-

<script type\="text/javascript" src\="/test/js/totop.js?v=1.0.0" async\=""\></script\>-
<script type\="text/javascript" src\="/test/js/toc.js?v=1.0.0" async\=""\></script\>-

### 新建Page报错

执行`hexo new page test`，然后`hexo clean && hexo g`，报错

1-
2-
3-
4-
5-
6-
7-
8-
9-
10-
11-
12-
13-
14-
15-
16-
17-
18-
19-
20-
21-
22-
23-
24-
25-
26-
27-
28-
29-

ERROR D:\\Documents\\test\\themes\\beantech\\layout\\page.ejs:56-
 54| ">-
 55|-
 >> 56| <%- page.content || body %\>-
 57|-
 58| <!-- 如果开启评论功能 -->-
 59| <% if(page.comments) { %\>-
-
body is not defined-
ReferenceError: D:\\Documents\\test\\themes\\beantech\\layout\\page.ejs:56-
 54| ">-
 55|-
 >> 56| <%- page.content || body %\>-
 57|-
 58| <!-- 如果开启评论功能 -->-
 59| <% if(page.comments) { %\>-
-
body is not defined-
 at eval (eval at compile (D:\\Documents\\test\\node\_modules\\ejs\\lib\\ejs.js:464:12), <anonymous>:69:32)-
 at returnedFn (D:\\Documents\\test\\node\_modules\\ejs\\lib\\ejs.js:493:17)-
 at Theme.\_View.View.\_compiled.locals \[as \_compiled\] (D:\\Documents\\test\\node\_modules\\hexo\\lib\\theme\\view.js:125:48)-
 at Theme.\_View.View.View.render (D:\\Documents\\test\\node\_modules\\hexo\\lib\\theme\\view.js:30:15)-
 at route.set (D:\\Documents\\test\\node\_modules\\hexo\\lib\\hexo\\index.js:394:29)-
 at tryCatcher (D:\\Documents\\test\\node\_modules\\bluebird\\js\\release\\util.js:16:23)-
 at D:\\Documents\\test\\node\_modules\\bluebird\\js\\release\\method.js:15:34-
 at RouteStream.\_read (D:\\Documents\\test\\node\_modules\\hexo\\lib\\hexo\\router.js:134:3)-
 at RouteStream.Readable.read (\_stream\_readable.js:454:10)-
 at resume\_ (\_stream\_readable.js:834:12)-
 at process.\_tickCallback (internal/process/next\_tick.js:178:19)-

此[issue](https://github.com/Haojen/hexo-theme-Anisina/issues/53)在其他主题中存在，[解决方法](https://fingthinking.github.io/2017/08/05/Hexo%E5%8F%8AAnisina%E4%BD%BF%E7%94%A8%E5%BF%83%E5%BE%97/):

*   将page.ejs重命名为m\_page.ejs
*   将index.ejs的layout替换为m\_page
*   新建page.ejs，内容为

1-
2-
3-
4-
5-

-
\----
layout: m\_page-
\----
<%- page.content %>-

所有命令如下:

1-
2-
3-
4-

cd ./themes/beantech/layout/-
mv page.ejs m\_page.ejs-
sed -i="" '2s/^.\*/layout: m\_page/' index.ejs-
echo -e "---\\nlayout: m\_page\\n---\\n<%- page.content %>" > page.ejs-

### 无法获得Post时间（未能复现）

遇到过一个Bug

1-

TypeError: (name || "").toLowerCase is not a function-

但是似乎高版本修复了，未能复现。可以参见[issue](https://github.com/hexojs/hexo/issues/3505)。是由于没有设置时区引起的。时区的写法参见[Wiki](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones)。

### 导航栏顺序不固定

是由于`./themes/beantech/layout/_partial/nav.ejs`中`site.pages`没有排序导致的。找到原本的代码

1-

<% site.pages.forEach(function(page){ %>-

修改为

1-

<% site.pages.data.sort(function(a, b) {return a.title > b.title}).forEach(function(page){ %>-

可以修复为按字母表排序。原来已经单独处理了Home保证在第一个。此外，我希望左上角导航到原本的个人主页，因此将同一文件的第12行改为了

1-

<a class\="navbar-brand" href="<%= config.root %>../index.html"\>Homepage</a>-

## 已知缺陷

### Contents为none会有滚动条

正常使用没有影响，不需要contents关掉就可以了。

### 主页摘要不支持`<!--more-->`

是一个open [issue](https://github.com/YenYuHsuan/hexo-theme-beantech/issues/5)，想改字数的话可以在`themes/beantech/layout/index.ejs`的17行。

* * *

## 部署到Github上

1-

hexo clean && hexo g && hexo d-

> Remark:-
> 依赖`npm install hexo-deployer-git --save`，之前已经装过了。

然后访问`<username>.github.io/test/`就可以看到了。

* * *

## 新建文章

基本命令是`hexo new [post/page/draft] "<title>"`，在config中默认了`default_layout: post`，因此也可以`hexo new "<title>"`来新建一篇文章。

## Post

执行后，会在`./source/_posts`目录中新建一个`<title>`文件夹与`<title>.md`文件。默认的格式来源于`./scaffolds/post.md`。添加tags的方式为

1-
2-
3-
4-
5-
6-
7-
8-

\----
...-
tags:-
\- Hexo-
\- Blog-
category:-
\- Hexo-
\----

文章书写依照Markdown语法，略。对于图片的引用直接放在同名文件夹下，没有前置地址。

## Page

新建Page类似于`about`/`tags`/`archive`等，会直接生成`./source/<title>/<index.md>`，套用的是`./scaffolds/page.md`。通常而言是不会用到的。

## Draft

一般用不到，新生成的draft不会显示，需要`hexo publish [layout] <title>`发布到`_posts`内，或者`hexo g --draft`/`hexo s --draft`预览。

## 后记

搭建网站的过程中还是新学了很多东西，比如ejs、md语法，html的调试等。目前还没有使用版本控制，后面应该会用git管理一下，需要删除本地`.git`文件夹，新建一个项目。但是由于部署方式也是git，会有比较麻烦的覆盖问题。网上给出的解决方法是直接拷贝。此外，还存在问题的点包括：

*   图片的管理方式（目前全在Github上，也许会超空间）。
*   未测试数学公式的使用。
*   留言系统的开放。-
    应该会弃坑一段时间，目前的功能已经足够我日常使用了。有问题或建议欢迎[email](mailto:yqiuac@cse.ust.hk)我。

* * *

*   [← Previous Post](https://qiutedyuan.github.io/blog/2019/06/12/Emacs%E5%B8%B8%E7%94%A8%E5%BF%AB%E6%8D%B7%E9%94%AE%E4%B8%80%E8%A7%88/)

[查看原网页: qiutedyuan.github.io](https://qiutedyuan.github.io/blog/2019/06/01/%E5%A6%82%E4%BD%95%E7%94%A8Hexo%E6%90%AD%E5%BB%BA%E4%B8%AA%E4%BA%BABlog/)
