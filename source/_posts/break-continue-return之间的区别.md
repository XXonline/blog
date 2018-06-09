---
title: break-continue-return之间的区别
date: 2017-04-07 22:44:31
tags: break/continue/return
categories: javaScript
---
## break

### break 语句用于退出 switch 语句或循环语句(for, for ... in, while, do ... while)。

当 break 语句用于 switch 语句中时，会跳出 switch 代码块(终止执行其代码)。如：

```javascript
var day;
switch (new Date().getDay()) {
    case 0:
        day = "Sunday";
        break;
    case 1:
        day = "Monday";
        break;
    case 2:
        day = "Tuesday";
        break;
    case 3:
        day = "Wednesday";
        break;
    case 4:
        day = "Thursday";
        break;
    case 5:
        day = "Friday";
        break;
    case 6:
        day = "Saturday";
        break;
}
console.log(day);
```



当 break 语句用于for循环语句时，(跳出整个循环体)会终止执行循环，并执行循环后代码(如果有的话)。如：

```javascript
(function (){
  var iSum = 0;
  for(var i = 1;i<101;i++){
    if(i == 5){
      break;
    }
    iSum +=i;
  }
  console.log(iSum); //10
}())
```

## continue

### continue 跳过`当前条件`的循环(用于跳过循环中的一个迭代，并继续执行循环中的下一个迭代)。



**continue** 与 **break**语句的`区别`是， **break** 是结束整个循环体， **continue **是结束单次循环。

`注意：`  **continue ** 语句（不带标签引用），只能用在循环或  switch 中。

```javascript
//在 while 循环中
var text = "";
var i = 0;
while (i < 5) {
    i++;
    if (i == 3) {
        continue;
    }
console.log(i); //1,2,4,5
}

//在 for 循环中
(function (){
  var iSum = 0;
  for(var i = 1;i<101;i++){
    if(i == 5){
      continue;
    }
    iSum +=i;
  }
  console.log(iSum); //5045
}())
```

## return

#### return表示(结束整个方法体)终止函数的执行并返回函数的值。

```javascript
//用法1
(function (){
  var iSum = 0;
  for(var i = 1;i<101;i++){
    if(i == 5){
      return;
    }
    iSum +=i;
  }
  console.log(iSum); //当i==5时，结束（return）了整个方法体，所以此时没有执行这行代码
}())

//用法2
(function (){
  var iSum = 0;
  for(var i = 1;i<101;i++){
    if(i == 5){
      //return;
      i = A(i);
    }
    iSum +=i;
  }
  console.log(iSum); //5015,i 跳过了5，6，7，8，9，此时的i设为了10
}())

function A(i){
  i+=5;
  return i; //i可选(非必填)。指定返回的函数值。如果忽略，A(i)函数将返回 undefined
}
```



## 总结：

#### break:跳出整个循环体

#### continue:跳过`当前条件`的循环

#### return：结束当前方法体







