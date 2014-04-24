---
layout: post
title: "PHP里的版本比较函数"
tagline: ""
description: ""
category: ""
tags: 
- php
- version
- compare
---
{% include JB/setup %}

关于版本比较函数，PHP函数strnatcmp与version_compare的不同如下：

	version_compare('10.4.1.RC2', '7.4.1.rc1') > 0
	//结果返回TRUE
	strnatcmp('10.4.1.RC2', '7.4.1.rc1') > 0
	//结果返回TRUE
	
	version_compare('7.4.1.RC2', '7.4.1.rc1') > 0
	//结果返回TRUE
	strnatcmp('7.4.1.RC2', '7.4.1.rc1') > 0
	//结果返回FALSE
	
如果版本里有字母，strnatcmp函数大小写会做判断，而version_compare则不是的。
