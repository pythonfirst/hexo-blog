---
title: freeCodeCamp算法中级：丢失的字母
date: 2020-07-19 20:32:21
tags: freeCodeCamp 前端 算法
---
##### 题目

> 在这道题目中，我们需要写一个函数，找到传入的字符串里缺失的字母并返回它。
>
> 判断缺失的依据是字母顺序，比如 abcdfg 中缺失了 e。而 abcdef 中就没有字母缺失，此时我们需要返回`undefined`。

##### 测试用例

```javascript
fearNotLetter("abce")应该返回 "d"。
fearNotLetter("abcdefghjklmno")应该返回 "i"。
fearNotLetter("stvwx")应该返回 "u"。
fearNotLetter("bcdf")应该返回 "e"。
fearNotLetter("abcdefghijklmnopqrstuvwxyz")应该返回undefined。
```

##### 解题思路

```javascript
function fearNotLetter(str) {
  let arr = str.split('')
  let num = 0
  for (let i=0; i<arr.length; i++) {
    console.log('num', num, 'code', arr[i].charCodeAt())
    if (!num) {
      num = arr[i].charCodeAt()
    } else {
      if (num === arr[i].charCodeAt()-1) {
        num++
      } else {
        console.log(String.fromCharCode(num++))
        return String.fromCharCode(num++)
      }
    }
  return undefined;
}
fearNotLetter("abce");
```

##### 知识点

```
String.fromCharCode()
str.charCodeAt()
```

