---
layout: post
title: "PHP中serialize和unserialize函数的一些探索"
tagline: ""
description: ""
category: ""
tags: 
- serialize 
- unserialize
- php
---
{% include JB/setup %}

业余时间开发一些个[PHP框架][1]之类的东西，其中用到了PHP序列化的两个重要函数，分别是`serialize()`和`unserialize()`，在没有参考[这里][2]的情况下自己做了一些小的测试探索，如下：

1. 序列化对象，然后再反序列化。结果很显然是正确的，且私有属性也被设置了值
2. 将序列化前的对象与反序列化后的对象进行比较，`==`时返回是true，`===`则返回false，测试代码如下，说明反序列化的过程也是一个实例化的过程

	$str = serialize($obj);
	$copy = unserialize($str);
	var_dump($obj == $copy);
	var_dump($obj === $copy)；

3. 如果对象是用单例模式实例化的，结果又是如何呢，与第2项测试结果相同，看来我们**可以使用反序列化来突破单例的限制**
4. 将序列化的字符串取出放在另一个PHP脚本进行反序列化，测试结果返回false。结果也是预料之中，类名找不到的
5. 如果我在PHP脚本中使用`spl_autoload_register()`注册了类自动加载函数，测试结果依然返回false。原来在php.ini中有`unserialize_callback_func`配置项，可以使用`ini_set()`注册，见[这里][3]。结果告诉我们不能想当然
6. 其他关于与魔术方法的关系这里没有进行深入测试比较

[1]: https://github.com/lay595715148/lay
[2]: http://www.php.net/manual/en/function.serialize.php
[3]: http://www.php.net/manual/en/var.configuration.php#unserialize-callback-func