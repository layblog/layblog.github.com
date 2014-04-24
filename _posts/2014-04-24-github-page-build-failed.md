---
layout: post
title: "GitHub个人主页发布新文章时报错：Page build failed"
tagline: ""
description: ""
category: ""
tags: 
- page
- bulid
- GithHub
---
{% include JB/setup %}

GitHub个人主页发布新文章时报错：Page build failed.

根据GitHub上给出的[帮助信息][1]，检查当前安装的相关软件版本号，再检查相关日期标题是否有填写错误，发现都没有问题，最后是检查md文件的编码时发现不是 `UTF-8`格式。因为我使用的是Nodepad++编辑器，在Windows下新建一个文件默认是ANSI编码的，所以只要将文件改成 `UTF-8` 编码格式就一切OK了

[1]: https://help.github.com/articles/using-jekyll-with-pages#troubleshooting](https://help.github.com/articles/using-jekyll-with-pages#troubleshooting
