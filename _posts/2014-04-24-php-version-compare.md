---
layout: post
title: "PHP��İ汾�ȽϺ���"
tagline: ""
description: ""
category: ""
tags: 
- php
- version
- compare
---
{% include JB/setup %}

���ڰ汾�ȽϺ�����PHP����strnatcmp��version_compare�Ĳ�ͬ���£�

	version_compare('10.4.1.RC2', '7.4.1.rc1') > 0
	//�������TRUE
	strnatcmp('10.4.1.RC2', '7.4.1.rc1') > 0
	//�������TRUE
	
	version_compare('7.4.1.RC2', '7.4.1.rc1') > 0
	//�������TRUE
	strnatcmp('7.4.1.RC2', '7.4.1.rc1') > 0
	//�������FALSE
	
����汾������ĸ��strnatcmp������Сд�����жϣ���version_compare���ǵġ�
