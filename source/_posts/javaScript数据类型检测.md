---
title: javascript数据类型检测
date: 2018-09-22 10:27
tags: javaScript
categories: javaScript
---
> 知识点：Object.prototype.toString.call(obj) === '[object typeStr]'; `typeStr`首字母必须大写
方法如下：
---

```javascript
/**
 * @desc 数据类型检测
 * @param obj 待检测的数据
 * @return {String} 类型字符串
 */
function jsType(obj) {
    var toString=Object.prototype.toString;
    var toType = {};
    var typeArr=['Undefined','Null','Boolean','Number','String','Object','Array','Function','Date','RegExp','Error','Arguments'];
    typeArr.map(function(item) {
        toType["[object " + item + "]"] = item.toLowerCase();
    });
    return typeof obj !== "object" ? typeof obj : toType[toString.call(obj)];
}
```




