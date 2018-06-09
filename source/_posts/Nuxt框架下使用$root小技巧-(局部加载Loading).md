---
title: Nuxt框架下使用$root小技巧-(局部加载Loading)
date: 2018-01-29 16:40:36
tags: Nuxt/Vue
categories: Vue
---
### **使用场景：**
- 在Vue（ssr）项目中，当用户进行交互的时，如果需要加上Loading动画（项目中Loading一般封装成了组件）时可以这样使用;               


### **使用方法：**
- 单页应用：在需要加载Loading组件的页面（这里的页面指components文件夹下面的组件）中，导入a.js直接调用即可;
- 多页应用：在pages目录下的需要加载Loading组件的页面中，导入a.js直接调用即可;^^^^^^^我是把js写在mixins里面的，当然也可以写在别的地方，比如utils中^^^^^^^


```javascript
// a.js
export default {
    methods: {
        showLoading() {
            this.$root.$children[0].loading = true
        },
        hideLoading() {
            this.$root.$children[0].loading = false
        }
    }
}
// xx.vue里面调用
import AMixin from '../../mixins/a'
export default {
    mixins: [AMixin],
    methods: {
        testFunc() {
            this.showLoading() // open
            this.hideLoading() // close
        }
    }
}
```



### **总结：**
1、这里主要考察的是对$root的灵活运用；
2、如果是全局页面跳转转场效果的话，Nuxt框架已经帮我们做了，我们直接自定义动画样式即可；此文提到的使用场景，我们就是复用这个组件