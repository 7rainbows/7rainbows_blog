---
title: js数组方法总结（一）
date: 2019-08-14 17:28:12
tags: JavaScript
categories: js数组方法
---
虽然关于js数组方法的总结网上一搜一大把，但还是想自己总结，强化一下基础。
<!--more-->
**Array.isArray()**  
判断某个值是不是数组  
```javascript
var persons = ['Jerry', 'Tom', 'Jhon'];  
console.log(Array.isArray(persons));  //true 
```
  
**toString(); valueOf()**  
js有五种基本数据类型和一种引用数据类型Object，Object的每个实例都有toString();valueOf()这两种方法，
而数组作为引用数据类型也有这两种方法。  
toString()  返回由数组中的每个值的字符串形式拼接而成的一个以逗号分隔的字符串 (这是人话么。。)  
```javascript
var persons = ['Jerry', 'Tom', 'Jhon'];  
var numbers = [1, 2, 3];  
console.log(persons.toString());  //Jerry,Tom,Jhon  
console.log(numbers.toString());  //'1','2','3'  
```
valueOf()  返回的还是原数组  
```javascript
var persons = ['Jerry', 'Tom', 'Jhon'];  
console.log(persons.valueOf());  //['Jerry', 'Tom', 'Jhon'];  
```

**push()**  
向数组最后添加一个或多个元素，改变原数组并返回改变后数组的长度。  
末尾添加，改变原数组，返回长度  
```javascript
var a = ['Jerry', 'Tom', 'Jhon'];  
var b = a.push('Bob');  
console.log(a);  //['Jerry', 'Tom', 'Jhon', 'Bob']  
console.log(b);  // 4  
```

**unshift()**  
向数组最前添加一个或多个元素，改变原数组并返回改变后数组的长度。  
首部添加，改变原数组，返回长度  
```javascript
var a = ['Jerry', 'Tom', 'Jhon'];  
var b = a.unshift('Bob');  
console.log(a);  //['Bob', 'Jerry', 'Tom', 'Jhon']  
console.log(b);  // 4  
```

**pop()**  
删除数组最后一个元素，改变原数组并返回所删除元素。  
末尾删除，改变原数组，返回被删元素，
```javascript
var a = ['Jerry', 'Tom', 'Jhon','Bob'];  
var b = a.pop();  
console.log(a);  //['Jerry', 'Tom', 'Jhon']  
console.log(b);  // Bob  
```

**shift()**  
删除数组第一个元素，改变原数组并返回所删除元素。  
首部删除，改变原数组，返回被删元素，
```javascript
var a = ['Jerry', 'Tom', 'Jhon','Bob'];  
var b = a.shift();  
console.log(a);  //['Tom', 'Jhon', 'Bob']  
console.log(b);  // Jerry  
```

**reverse()**  
颠倒数组中元素的顺序，改变原数组。
改变原数组，返回颠倒后的数组。
```javascript
var a = [1, 2, 3, 4 ,5];  
var b = a.reverse();  
console.log(a);  //[5, 4, 3, 2, 1]  
console.log(b);  //[5, 4, 3, 2, 1]  
```

**sort()**  
按ascii码排序
改变原数组，返回排序后的数组。
```javascript
var a = [0, 1, 15, 5, 10];  
var b = a.sort();  
console.log(a);  //[0, 1, 10, 15, 5]  
console.log(b);  //[0, 1, 10, 15, 5]  
```
然而这种结果往往不是我们想要的，那么怎样可以使其按照数字大小来排序呢？  
sort()方法可以接收一个比较函数作为参数，  
```javascript
function compare(value1, value2) {
    if (value1 < value2) {
	return -1;
    } else if (value1 > value2) {
	return 1;
    } else {
	return 0;
    }
}
var a = [0, 1, 15, 5, 10];  
var b = a.sort(compare);  
console.log(a);  //[0, 1, 5, 10, 15] 
console.log(b);  //[0, 1, 5, 10, 15]
```
上面这个例子就实现了数值的正序排序，倒序只需将比较函数中的返回值交换即可。  

**concat()**  
基于当前数组创建一个副本，并将接收的参数添加到这个副本的末尾，最后返回创建的副本数组，并不会对原数组引用。  
如果接收的参数是数组，则将参数数组拼接到原数组的末尾，并返回新数组，如果没有参数，则复制原数组，返回副本。
原数组不变，返回新数组。  
```javascript
var a = ["Jerry", "Tom", "Jhon"];  
var b = ["Bob", "Lily"];
var c = "Mary";

var d = a.concat(b);  
var e = a.concat(b, c);
var f = a.concat({name: "Jack"});
console.log(a);  //["Jerry", "Tom", "Jhon"]
console.log(b);  //["Bob", "Lily"]
console.log(d);  //["Jerry", "Tom", "Jhon", "Bob", "Lily"]
console.log(e);  //["Jerry", "Tom", "Jhon", "Bob", "Lily", "Mary"]
console.log(f);  // ["Jerry", "Tom", "Jhon", {name: "Jack"}]
```

**slice()**  
slice(startIndex,endIndex)  返回从startIndex开始(包括)，到endIndex(不包括)之间的元素组成的数组  
slice(startIndex)  返回从startIndex开始(包括)到数组末尾的所有元素组成的数组  
slice()  返回从startIndex开始(包括)，到endIndex(不包括)之间的元素组成的数组