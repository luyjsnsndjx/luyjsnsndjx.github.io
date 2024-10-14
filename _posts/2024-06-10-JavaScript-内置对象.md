---
layout:     post
title:      JavaScript
subtitle:   内置对象
date:       2024-06-10
author:     XiaoLei
header-img: /img/post-bg-article.jpg
catalog: true
tags:
    - Git
---
## 前言
在JavaScript的世界里，一切都是对象。

但是某些对象还是和其他对象不太一样。为了区分对象的类型，我们用typeof操作符获取对象的类型，它总是返回一个字符串：
```
typeof 123; // 'number'
typeof 123n; // 'bigint'
typeof NaN; // 'number'
typeof 'str'; // 'string'
typeof true; // 'boolean'
typeof undefined; // 'undefined'
typeof Math.abs; // 'function'
typeof null; // 'object'
typeof []; // 'object'
typeof {}; // 'object'
```
可见，number、bigint、string、boolean、function和undefined有别于其他类型。特别注意null的类型是object，Array的类型也是object，如果我们用typeof将无法区分出null、Array和通常意义上的object——{}。

## 包装对象
除了这些类型外，JavaScript还提供了包装对象

number、boolean和string都有包装对象。没错，在JavaScript中，字符串也区分string类型和它的包装类型。包装对象用new创建：
```
let n = new Number(123); // 123,生成了新的包装类型
let b = new Boolean(true); // true,生成了新的包装类型
let s = new String('str'); // 'str',生成了新的包装类型
```
虽然包装对象看上去和原来的值一模一样，显示出来也是一模一样，但他们的类型已经变为object了！所以，包装对象和原始值用===比较会返回false：
```
typeof new Number(123); // 'object'
new Number(123) === 123; // false

typeof new Boolean(true); // 'object'
new Boolean(true) === true; // false

typeof new String('str'); // 'object'
new String('str') === 'str'; // false


typeof new Boolean(true); // 'object'
new Boolean(true) === true; // false

typeof new String('str'); // 'object'
new String('str') === 'str'; // false
```
