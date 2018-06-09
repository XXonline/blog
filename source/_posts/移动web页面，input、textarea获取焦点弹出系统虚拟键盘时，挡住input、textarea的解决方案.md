---
title: 移动web页面，input、textarea获取焦点弹出系统虚拟键盘时，挡住input、textarea的解决方案
date: 2017-04-07 20:58:32
tags: scrollIntoView()、scrollIntoViewNeeded()
categories: javaScript
---
### **使用场景**
- 在移动web页面里，当点击input、textarea获取到焦点弹出系统虚拟键盘后，虚拟键盘挡住了输入框的情况；这种问题一般出现在部分android机型中，在ios机型中一般不会出现这个问题
- 在移动web页面里，只有可以滑动的时候就可以使用这个方法处理一些类似于锚点的问题，并非一定是输入框才可以使用 


### **解决方案**
- 通过js动态处理；在元素（输入框）被操作后，若元素在可视区域内，则不做处理。反之通过js将该元素的位置移动到可视区域内即可 
- 使用W3C标准的scrollIntoView()、scrollIntoViewNeeded()方法处理,该方法就是让当前的元素滚动到浏览器窗口的可视区域内；两个方法共同使用可以兼容大部分的浏览器（移动端），该方法的参数类型是boolean值，默认参数是true。如果为true，元素的顶端将和其所在滚动区的可视区域的顶端对齐。反之，元素的底端将和其所在滚动区的可视区域的底端对齐。 


### **使用方法** 
- 原生js里面 
```javascript
<body>
    <div class="chunk"></div>
    <div class="scrollIntoView">scrollIntoView top</div>
    <div class="scrollIntoViewIfNeeded-top">scrollIntoViewIfNeeded top</div>
    <div class="scrollIntoViewIfNeeded-bottom">scrollIntoViewIfNeeded botom</div>
    <script>
    const scrollIntoView = document.querySelector('.scrollIntoView');
    const scrollIntoViewIfNeededTop = document.querySelector('.scrollIntoViewIfNeeded-top');
    const scrollIntoViewIfNeededBottom = document.querySelector('.scrollIntoViewIfNeeded-bottom');
    const test = document.querySelector('.chunk');
    scrollIntoView.addEventListener('click', function() {
      test.scrollIntoView(true);
    });
    scrollIntoViewIfNeededTop.addEventListener('click', function() {
      test.scrollIntoViewIfNeeded(true);
    });
    scrollIntoViewIfNeededBottom.addEventListener('click', function() {
      test.scrollIntoViewIfNeeded(false);
    });
    </script>
</body>
```
- vue里面 
```vue
<template>
    <li class="requirement-description">
        <div class="li-inner">
            <span>测试数据</span>
            <textarea maxlength="200"
                      name="textarea"
                      @focus="textAreaFocus"
                      ref="textAreaF"></textarea>
        </div>
    </li>
</template>
<script>
    export default {
        name: 'Item-Textarea',
        methods: {
            textAreaFocus() {
                this.$refs.textAreaF.scrollIntoView(false)
                this.$refs.textAreaF.scrollIntoViewIfNeeded(false)
            }
        }
    }
</script>
```