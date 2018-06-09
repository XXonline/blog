---
title: JS中innerHTML、outerHTML、innerText、outerText的用法与区别
date: 2017-05-03 19:58:49
tags: innerHTML、outerHTML、innerText、outerText
categories: javaScript
---
--转自[http://blog.163.com/yw_0721/blog/static/7164579720102932157759/](http://blog.163.com/yw_0721/blog/static/7164579720102932157759/)

在JS中可以使用：
![img](http://img.ph.126.net/w-wNA1rVd-dnL69Mi1cHcA==/3255258105659357017.jpg?_=2768532)
### innerHTML:
也就是从对象的起始位置到终止位置的全部内容,包括Html标签。
### innerText:
从起始位置到终止位置的内容, 但它去除Html标签。
### outerHTML:
除了包含innerHTML的全部内容外, 还包含对象标签本身。
### outerText:
设置(包括标签)或获取(不包括标签)对象的文本 。
**示例：**
```html
<div id="test">
      <span style="color:red">test1</span> test2
</div>
```
```javascript
<a href="javascript:alert(test.innerHTML)">innerHTML内容</a>
<a href="javascript:alert(test.innerText)">innerText内容</a>
<a href="javascript:alert(test.outerHTML)">outerHTML内容</a>
```
###特别说明：
innerHTML是符合W3C标准的属性，而innerText只适用于IE浏览器，因此，尽可能地去使用innerHTML，而少用innerText，如果要输出不含HTML标签的内容，可以使用innerHTML取得包含HTML标签的内容后，再用正则表达式去除HTML标签，下面是一个简单的符合W3C标准的示例：
```javascript
<a href="javascript:alert(document.getElementById('test').innerHTML.replace(/<.+?>/gim,''))">无HTML,符合W3C标准</a>
```
