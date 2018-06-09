---
title: opacity和visiblity
date: 2017-09-10 20:58:32
tags: css
categories: javaScript
---
- `opacity`:设置父元素隐藏，设置子元素显示将`失效`
- `visiblity`:设置父元素隐藏，设置子元素显示将`成功`
```javascript
.item1 {
    width: 400px;
    height: 400px;
    padding: 100px;
    box-sizing: border-box;
    background-color: green;
    text-align: center;
    /*opacity: 0;*/
    visibility: hidden
}
.item2 {
    width: 200px;
    height: 200px;
    background-color: fuchsia;
    /*opacity: 1;*/
    visibility: visible
}
<div class="item1">
    <div class="item2"></div>
</div>
```
