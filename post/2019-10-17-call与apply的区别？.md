---
showonlyimage: true
title:      "apply与call的区别？"
subtitle:   ""
excerpt: ""
description: "appLy与call的区别？哪个性能更佳？"
date:       2019-06-04
author:     "SKwings"
image: "https://img.zhaohuabing.com/in-post/2018-06-04-introducing-the-istio-v1alpha3-routing-api/background.jpg"
published: true 
tags:
    - javaScript
    - apply 
    - call
categories: [ Tech ]
URL: ""
---

# 区别？

call的性能要比apply好一些（尤其是传递给函数的参数超过三个的时候），所以后期开发的时候，可以使用call多一点。
```
fuction.call(obj,10,20,30);  
function.apply(obj,[10,20,30])//apply()传参时，以数组形式传递给对象。
```

## Call()

call() 方法
call() 方法是与经典的对象冒充方法最相似的方法。它的第一个参数用作 this 的对象。其他参数都直接传递给函数自身。例如：

```
function sayColor(sPrefix,sSuffix) {
    alert(sPrefix + this.color + sSuffix);
};

var obj = new Object();
obj.color = "blue";

sayColor.call(obj, "The color is ", "a very nice color indeed.");
```
在这个例子中，函数sayColor（）在外定义，即使他不属于任何对象，也可以引用关键字this。调用call（）方法时，第一个参数是obj，所以this指向的是obj。第二和第三个参数是字符串，与saycolor（）函数中的sPrefix和sSuffix匹配。  
最后的结果是 **“The color is blue ，a very nice color indeed.”**

## apply()

apply() 方法有两个参数，用作 this 的对象和要传递给函数的参数的数组。例如：

```
function sayColor(sPrefix,sSuffix) {
    alert(sPrefix + this.color + sSuffix);
};

var obj = new Object();
obj.color = "blue";

sayColor.apply(obj, new Array("The color is ", "a very nice color indeed."));

```
在这个例子中，函数 sayColor() 在对象外定义，即使它不属于任何对象，也可以引用关键字 this。对象 obj 的 color 属性等于 blue。调用 call() 方法时，第一个参数是 obj，说明应该赋予 sayColor() 函数中的 this 关键字值是 obj。第二个和第三个参数是字符串。它们与 sayColor() 函数中的参数 sPrefix 和 sSuffix 匹配，最后生成的消息 **"The color is blue, a very nice color indeed." 将被显示出来。**