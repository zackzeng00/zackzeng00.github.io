---
title:  Hexo如何fork主题
date: 2021-7-13
tags: 
  - 教程
  - Hexo
---
## Hexo 主题更新的痛点
  最初使用更换主题用的最多的办法是是将主题theme下载下来，解压到site目录下。这样使用会带来一个问题。
- 后续主题git有更新的时候，需要更新theme的时候，需要手动下载文件覆盖更新，并且需要注意config文件的保存

## 解题思路
  经过搜索一番优雅的更新主题呢？尝试解决一下 一共分为几步
1. Fork 主题git，因为你需要更改里面文件为了保证你有这个仓库的主导权，所以fork一份。
2. 通过Git submodules ，在你的site仓库下，作为一个子仓库加入你的项目。
3. 后续使用git 自动更新主题


#### Fork一份参考
  这一步主要目的，是为了有一份自己可以修改的主题仓库，主要用的办法不熟悉git命令，那就直接到web页面点击

#### 添加一个子仓库

```
git submodule add https://github.com/cofess/hexo-theme-pure themes/pure

```

#### 后续更新
> 我自己还没研究明白，
> 留白待续

