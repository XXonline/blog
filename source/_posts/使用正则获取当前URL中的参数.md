---
title: 使用正则获取当前URL中的参数
date: 2017-06-09 20:58:32
tags: URL
categories: javaScript/正则表达式
---
 **使用场景：**在前台，当需要通过当前url这个的参数处理一些逻辑的时候，可以使用此方法。
 **函数如下：**
```javascript
function getQueryString(name) {
    var reg = new RegExp("(^|&)" + name + "=([^&]*)(&|$)", "i");
    var r = window.location.search.substr(1).match(reg);
    if (r != null) return unescape(r[2]);
    return null;
}
```
**使用方法：**name-参数名称为字符串形式。若当前链接后面的参数为`?name=itonline&sex=gg&age=18`，则获取name参数值的调用方式为：`getQueryString("name")`;
