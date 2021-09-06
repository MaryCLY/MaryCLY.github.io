---
title: 牛客错题簿-JS
date: 2021-09-01 02:47:29
tags: JS
categories: JS
---

JavaScipt是一门单线程的语言。

解释：因为用于页面交互和操作DOM，多线程会导致各种同步错误。为了利用多核CPU的计算能力，HTML5提出Web Worker标准，允许JavaScript脚本创建多个线程，但是子线程完全受主线程控制，且不得操作DOM。所以，这个新标准并没有改变JavaScript单线程的本质。
<!--more-->
---

```JavaScript
null instanceof Object;
// false : null 的原型不是Object，但是typeof null返回object是某种规定
NaN == NaN;
// false : NaN是一个过于笼统的概念，不知道究竟表示的是什么数，因此不管是==或===都不相等
```

---

表单的JS选择：
```JavaScript
window.onload = function(){
    //首先获得下拉框的节点对象；
    var obj = document.getElementById("obj");
    //1.如何获得当前选中的值？：
    var value = obj.value;
    //2.如何获得该下拉框所有的option的节点对象
    var options = obj.options;
    //注意：得到的options是一个对象数组
    //3.如何获得第几个option的value值?比如我要获取第一option的value,可以这样：
    var value1 =options[0].value;
    //4.如何获得第几个option的文本内容?比如我要获取第一option的文本,可以这样：
    var text1 = options[0].text;
    //5.如何获得当前选中的option的索引？
    var index = obj.selectedIndex;
    //6.如何获得当前选中的option的文本内容？
    //从第2个问题，我们已经获得所有的option的对象数组options了
    //又从第5个问题，我们获取到了当前选中的option的索引值
    //所以我们只要同options[index]下标的方法得到当前选中的option了
    var selectedText =options[index].text;
}
```

---

```JavaScript
var datas=[10,20,30];
datas.unshift(40,50); datas.pop();
datas.push(60,70); datas.shift();
console.log(datas.toString());
```
输出的结果应该是：50,10,20,60,70;

解释：unshift和push如果携带多个参数，属于在头和尾合并这样一个数组，而非按顺序执行。

---

参考[Array.prototype.sort()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/sort)

Array.sort()的比较函数的意义是：
compareFunction(a, b)：
  * return<0, a排列在b之前；
  * return=0, 相对位置不变；
  * return>0, a排列在b之后；

所以如果要数字升序，可以使用a-b作为比较函数；降序，则使用b-a；

```JavaScript
var numbers = [4, 2, 5, 1, 3];
numbers.sort(function(a, b) {
  return a - b;
});
console.log(numbers);

// 也可以写成：
var numbers = [4, 2, 5, 1, 3];
numbers.sort((a, b) => a - b);
console.log(numbers);

// [1, 2, 3, 4, 5]
```
---

JavaScript正则表达式内容：

以下代码的执行后，str 的值是：
```JavaScript
var str = "Hellllo world";
str = str.replace(/(l)\1/g, '$1');
```
[String.prototype.replace](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/replace)
其中$1意为第1个括号选取的字符串，也就是l；

[正则表达式](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Guide/Regular_Expressions)语法中，
\1也意为第1个括号选取的字符串，也就是l；
而/.../g，即全局标签g，会进行全局匹配，也就是多次选取。

因此实际上的过程是：正则表达式全局选取"ll"，选中了两个"ll"，然后分别替换为"l"；最终的结果就是"Hello world"。

---

Date.now()返回的是一个毫秒数，也就是Number。而new Date({Number})可以根据时间戳创建一个Date对象。

---

JavaScript内部对象：
  * History 包含用户（在浏览器窗口中）访问过的 URL
  * Location 包含有关当前 URL 的信息
  * Window 表示浏览器中打开的窗口
  * Navigator 包含有关浏览器的信息

---

以下代码执行后，控制台的输出是：
```JavaScript
var a = 10;
function a(){}
console.log(typeof a)
```
函数提升大于变量提升，变量提升会提升到除函数声明的后面，这个过程等价于：
```JavaScript
function a(){}
var a; //顺便一提，var可以进行重声明，但let不能，如果let a会报错。
a = 10;
console.log(typeof a)
```
所以结果是"Number"

---

关于this对象：
  * 在不改变this指向的前提下，this总是指向函数的直接调用者。
  * 如果有new关键字，this指向new出来的那个对象。
  * IE中attachEvent中的this总是指向全局对象Window。

---

下列函数哪些是JavaScript的全局函数？
正确：encodeURI, parseFloat, eval
错误：setTimeOut
因为setTimeOut是window的函数。

---

parseInt的转换方式：
1、如果都是字母， 返回：NaN
parseInt("abc", 10)  //返回 NaN
2、如果都是数字，则返回整数
parseInt("123", 10)   //返回 123
3、如果字母和数字都存在
(1)、以数字开头，则取截止到第一个字母出现之前的所有数字进行转换
parseInt("12x2bc", 10)   // 返回：12
(2)、如果参数“string”，以字母开头，直接返回NaN （10进制中字母不是一个有效的的表示）
parseInt("df2bc", 10)  //返回 NaN

---

