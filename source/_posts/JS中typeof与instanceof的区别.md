---
title: JS中typeof与instanceof的区别
date: 2017-04-07 16:40:36
tags: typeof/instanceof
categories: javaScript
---
###  JavaScript 中 typeof 和 instanceof 常用来判断一个变量是否为空，或者是什么类型的。区别：
###  typeof

  typeof 是一个一元运算，放在一个运算数之前，运算数可以是任意类型。
  它返回值是一个字符串，该字符串说明运算数的类型。typeof 一般只能返回如下几个结果：
  number,boolean,string,function,object,undefined。我们可以使用 typeof 来获取一个变量是否存在，如 if(typeof a!="undefined"){alert("ok")}，而不要去使用 if(a) 因为如果 a 不存在（未声明）则会出错，对于 Array,Null 等特殊对象使用 typeof 一律返回 object，这正是 typeof 的局限性。
### instanceof
  instanceof 用于判断一个变量是否某个对象的实例，如:
  ```javascript
        //判断a是否是Array的实例
        var a = new Array();
        console.log(a instanceof Array); //true
        console.log(window instanceof Object); //true
        //所以，这里的 instanceof 测试的 object 是指 js 语法中的 object，不是指 dom 模型对象。
        console.log(a instanceof object); //true, 因为 Array 是 object 的子类

        //判断a是否是test的实例
        function test(){};
        var a=new test();
        console.log(a instanceof test); //true

         // 判断 foo 是否是 Foo 类的实例 , 并且是否是其父类型的实例
         function Aoo(){}
         function Foo(){}
         Foo.prototype = new Aoo();//JavaScript 原型继承

         var foo = new Foo();
         console.log(foo instanceof Foo)//true
         console.log(foo instanceof Aoo)//true
         //instanceof 复杂用法
         console.log(Object instanceof Object);//true
         console.log(Function instanceof Function);//true
         console.log(Number instanceof Number);//false
         console.log(String instanceof String);//false
         console.log(Function instanceof Object);//true
         console.log(Foo instanceof Function);//true
         console.log(Foo instanceof Foo);//false
  ```
   未完待续...
