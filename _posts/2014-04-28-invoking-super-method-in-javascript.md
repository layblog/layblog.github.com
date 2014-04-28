---
layout: post
title: "如何在Javascript子类方法中调用父类方法"
tagline: ""
description: ""
category: ""
tags: 
- javascript
- nodejs
- super
---
{% include JB/setup %}

如何在Javascript子类方法中调用父类方法，在[这里][1]有讲解多种方式的实现，就不一一赘述了。

上述文章中并没有在Nodejs下使用了`util.inherits()`继承的实现方式，如果我有多次继承时上述中实现方法将会不能使用或不易实现且代码量将会很大。参照Crockford的方法对inhertis方法做了一些改进如下：

	var inherits = util.inherits;
	
	util.inherits = function(Sub, Sup) {
	    var d = 0, p = Sup.prototype;
	    inherits(Sub, Sup);
	    Sub.prototype.super = function(name) {
	        var v = Sup.prototype, str = '' + Sub.prototype[name];
	        while(str && '' + v[name] === str) {
	            v = Object.getPrototypeOf(v);
	        }
	        return v[name].apply(this, Array.prototype.slice.apply(arguments, [1]));
	    };
	};

每个子类都会增加`super(name)`方法，使用了Function转字符串的特性，name参数是必选项。

[1]: http://www.blogjava.net/zhhp1314520/articles/js_child_parent.html