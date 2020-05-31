---
title: freeCodeCampz之算法中级：短线连接格式
date: 2020-05-29 21:49:00
tags: freeCodeCamp 前端 算法
---
##### 题目

> 在这道题目中，我们需要写一个函数，把一个字符串转换为“短线连接格式”。短线连接格式的意思是，所有字母都是小写，且用-连接。比如，对于Hello World，应该转换为hello-world；对于I love_Javascript-VeryMuch，应该转换为i-love-javascript-very-much。
##### 测试用例
```
spinalCase("This Is Spinal Tap") // "this-is-spinal-tap"
spinalCase("thisIsSpinalTap")  // "this-is-spinal-tap"
spinalCase("The_Andy_Griffith_Show") //"the-andy-griffith-show"
spinalCase("Teletubbies say Eh-oh") //spinalCase("Teletubbies say Eh-oh")
spinalCase("AllThe-small Things") // "all-the-small-things"
```
##### 解题思路
###### 思路1
看到题目后，首先想到`String.split()/String.join()/String.toLowerCase()`方法。当然这不是本题的难点。本题的难点在于如何将字符串正确的转为数组。因为测试字符串有以下划线 _ 分隔，有以空格分隔，有以中划线 - 分隔，甚至还有 `camelCase`,这样就只能用正则来将字符串分解为数组。

刚开始我写的 regex 是这样的：
```
 let pattern = /([a-zA-Z]+)/g
```
使用这个 `pattern` 加上 `String.match()`方法可以将字符串的单词分割成数组。这样如果没有遇到 `camelCase`还可以，碰到 `camelCase`就无法将string 正确转为数组。
###### 思路2
另外一个思路使用 `String.split(regexExp)`, 分隔符参数使用正则表达式来获取，其中camelCase使用正则的正向先行断言来处理。 
```
pattern = /\s|_|-|(?=[A-Z])/

"This Is Spinal Tap".split(pattern) // ["This", "Is", "Spinal", "Tap"]
"thisIsSpinalTap".split(pattern) //["this", "Is", "Spinal", "Tap"]
"The_Andy_Griffith_Show".split(pattern) // ["The", "Andy", "Griffith", "Show"]
"Teletubbies say Eh-oh".split(pattern) // ["Teletubbies", "say", "Eh", "oh"]
"AllThe-small Things".split(pattern) ["All", "The", "small", "Things"]
```
将字符串转为数组之后就可以使用 `String.join('-')` 方法重新连接字符串,最后对字符串使用 `String.toLowerCase()` 方法将大写字母转为小写字母。
```
function spinalCase(str) {
  let strs=str.split(/\s|-|_|(?=[A-Z])/).join('-').toLowerCase()
  return strs;
}
```
###### 思路3
还有一个思路使用两次 `String.replace()` 方法，第一次将 `_`、`' '`替换掉，如果遇到 `camelCase` 直接再使用针对 `camelCase` replace 方法。
```
"thisIsSpinalTap"replace(/\s|_/g, '-').replace(/([a-z])([A-Z])/g, '$1-$2').toLowerCase()
```


##### 总结
1. 正则表达式正向先行断言
2. 正则表达式级联使用。

##### 参考
1. [String.prototype.split\(\)--MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/split)
2. [Array.protoptype.join\(\)--MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/join)
3. [String.prototype.replace\(\)--MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/replace)
4. [正则表达式断言--MDN](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Guide/Regular_Expressions/Assertions)