---
title: 牛客错题簿-HTML
date: 2021-09-01 02:46:56
tags: HTML
categories: HTML
---

section标签：Html5语义化后的新标签，表示将一大块内容分成几个部分。
<!--more-->
---

noscript标签：如果脚本未执行（如浏览器未支持JavaScript脚本），则会显示标签里的内容。
```HTML
<script type="text/javascript">
	<!--
	document.write("Hello World!")
	//-->
</script><noscript>Your browser does not support JavaScript!</noscript>
```
---

[HTMLFormElement.enctype](https://developer.mozilla.org/zh-CN/docs/Web/API/HTMLFormElement/enctype)属性常用来指明提交表单的内容类型，可选的值如下：
  * application/x-www-form-urlencoded: 初始的默认值，在发送前编码所有字符
  * multipart/form-data:  不对字符编码，适用于使用\<input> 标签上传文件
  * text/plain: HTML5 引入的类型，空格转换为 "+" 加号，但不对特殊字符编码

这些值可以通过元素 \<button> or \<input> 的属性form.enctype来改写。

---

\<head>是文章的头部，\<slider>是侧边栏，\<main>是主要内容，\<footer>是尾部。

---

input属于窗体元素,层级显示比flash、其它元素都高。请判断这句话的正确与否。（错误）

解释：在HTML中，帧元素（frameset）的显示优先级最高，其次是表单元素，然后是非表单元素。flash属于帧元素，优先级更高。input属于窗体元素是正确的。

---

Canvas和SVG的不同点：

Canvas
  * 依赖分辨率
  * 不支持事件处理器
  * 弱的文本渲染能力
  * 能够以 .png 或 .jpg 格式保存结果图像
  * 最适合图像密集型的游戏，其中的许多对象会被频繁重绘
  * Canvas 是逐像素进行渲染的。
  * 在 Canvas 中，一旦图形被绘制完成，它就不会继续得到浏览器的关注。如果其位置发生变化，那么整个场景也需要重新绘制，包括任何或许已被图形覆盖的对象。

SVG
  * 不依赖分辨率
  * 支持事件处理器
  * 最适合带有大型渲染区域的应用程序（比如谷歌地图）
  * 复杂度高会减慢渲染速度（任何过度使用 DOM 的应用都不快）
  * 不适合游戏应用

---

input中的滑块控件type是range（理解成了slider，但slider是侧边栏）。

---

[HTML的全局属性](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Global_attributes)：所有标签都可以使用的属性。
比如style, id, class等等。

---

什么情况会创建块格式化上下文 BFC（一个隔离的容器，容器里的子元素不会影响到外面的元素）

https://developer.mozilla.org/zh-CN/docs/Web/Guide/CSS/Block_formatting_context

---

不能被冒泡的9个事件：load和unload、 mouseenter和mouseleave、 blur和focus、 error、 resize和abort

---

\<a>可以包含任何其他元素，但不能包含\<a>本身。

---

Dom Tree的根节点是Document对象。

---