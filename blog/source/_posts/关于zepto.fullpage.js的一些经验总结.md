---
title: 关于zepto.fullpage.js的一些经验总结
date: 2018-04-19 21:18:23
tags: zepto
categories: zepto,zeptoFullPage.js
description: 关于zepto.fullpage.js的一些经验总结
---

---
<h1>关于zepto.fullpage.js的一些经验总结</h1>
<p>
因为最近在做一个H5的小页面，页面需要用到整屛滑动，因为以前用过zepto.fullpage.js，所以就用它来做了
不过在做的过程中也发现了几个小问题
</p>
<p>1.在安卓手机下，页面中如果有input输入框，只要输入框获取了页面焦点，滑屏事件就会失效，但是滑动事件是有效的，只是不能整屛滑动事件就失效了，
解决方案是在安卓手机中，使用swipeUp还有swipeDown去控制fullpage的nextpage与prevpage。

</p>

``` js
$('.class').swipeUp(()=>{
    $.fn.fullpage.moveNext();
})
$('.class').swipeUp(()=>{
    $.fn.fullpage.movePrev();;
})
```
<p>
使用了zeptofullpage.js后如果页面有overFlow:scroll，sroll会失效，出现不能滑动滚动栏的情况，
解决方案是在该节点激活是时设置
```js
    $.fn.fullpage.stop();
```
关闭全屏滚动事件
</p>

