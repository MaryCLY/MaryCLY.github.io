---
title: 牛客错题簿-CSS
date: 2021-09-01 02:47:04
tags: CSS
categories: CSS
---

CSS选择器的权重（赋属性时的覆盖优先级）：
  * style: 1000 （HTML中的行内样式）
  * id: 100 （#id{}）
  * class: 10 （.class{}）
  * element: 1 （element{}）

<!--more-->
---

[CSS盒模型](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Building_blocks/The_box_model)：
  * 块级盒子和内联盒子
  * 标准盒模型（content-box）和替代（奇异/IE）盒模型（border-box）
  * 盒子内的部分
    - content: 内容。在content-box中设置的宽和高就是内容的宽高。会应用该元素的背景。
    - padding: 内边距。边框与内容区域之间的部分，增加内边距可以让边框和内容之间更宽敞。不能设置负值。内边距会应用该元素的背景。
    - border: 边框。内边距以外的部分。如果要设置边框，一定要设置大小和样式，否则不会生效。当设置为solid时，边框实际上是四个等腰梯形均分边框外界和内边距外界两个矩形之间的空间。因此当内容和内边距的面积都是0的时候，就会变成均分一个矩形，也就是四个三角形。由此可以实现将内容设为0，某些边框设为透明来显示三角形。
    - margin: 外边距。在border以外的矩形部分，用来推开其他盒子。如果设置负值，则会向其他盒子重叠。会显示父元素的背景（因为是透明的）。两个紧挨的外边距会出现折叠的情况，通常只会设定成两个里面的较大值。
  * 不管是padding, border, 还是margin, 他们的大小设置百分比时都是参照父元素的宽度。
  * 当使用padding或margin属性设置时：
    - padding: 10px; 上下左右全部设为10px;
    - padding: 10px 2px; 上下设为10px, 左右设为2px;
    - padding: 2px 3px 4px; 上设为2px, 左右设为3px, 下设为4px;
    - padding: 2px 3px 4px 5px; 上右下左（顺时针）分别设置。

---

改变一个元素状态CSS属性的排列顺序可以改变显示优先级，在后的会优先显示。

题目：超链接访问过后hover样式就不出现了，被点击访问过的超链接样式不再具有hover和active了，解决方法是改变CSS属性的排列顺序？

答案：a:link {} a:visited {} a:hover {} a:active {}

---

word-break属性可以调整是否为整个单词换行，[white-space](https://developer.mozilla.org/zh-CN/docs/Web/CSS/white-space)属性可以设定是否以及在哪些地方自动换行，所以严格来说如果要设置不换行应该设置white-space（可以设为nowrap）。

---

CSS选择器中，nth-child是从1开始数的。

---

CSS中link和@import的区别:
  * link属于XHTML标签，而@import完全是CSS提供的一种方式。
  * 当一个页面被加载的时候，link引用的CSS会同时被加载，而@import引用的CSS会等到页面全部被下载完再被加载。
  * link在支持CSS的浏览器上都支持而@import只在5.0以上的版本有效。
  * 当使用javascript控制dom去改变样式的时候，只能使用link标签，因为@import不是dom可以控制的。

---

