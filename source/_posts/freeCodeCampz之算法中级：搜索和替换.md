---
title: freeCodeCampz之算法中级：搜索和替换
date: 2020-05-31 23:45:07
tags: freeCodeCamp 前端 算法
---
##### 题目
> 在这道题目中，我们需要写一个字符串的搜索与替换函数，它的返回值为完成替换   后的新字符串。
> 
> 这个函数接收的第一个参数为待替换的句子.
  第二个参数为句中需要被替换的单词。
  第三个参数为替换后的单词。
>
>  注意：你需要保留被替换单词首字母的大小写格式。即如果传入的第二个参数为 "Book"，第三个参数为 "dog"，那么替换后的结果应为 "Dog"

##### 测试用例
```
myReplace("Let us go to the store", "store", "mall")应该返回 "Let us go to the mall"。
Passed
myReplace("He is Sleeping on the couch", "Sleeping", "sitting")应该返回 "He is Sitting on the couch"。
Passed
myReplace("This has a spellngi error", "spellngi", "spelling")应该返回 "This has a spelling error"。
Passed
myReplace("His name is Tom", "Tom", "john")应该返回 "His name is John"。
Passed
myReplace("Let us get back to more Coding", "Coding", "algorithms")应该返回 "Let us get back to more Algorithms"。
```

##### 解题思路
```
function myReplace(str, before, after) {
  if (/[A-Z]/.test(before[0])) {
    if (/[a-z]/.test(after[0])) {
      after = after.replace(/([a-z])/, $1=>$1.toUpperCase())
    }
  } else {
    if (/[A-Z]/.test(after[0])) {
      after = after.replace(/[A-Z]/,$1=>$1.tuLowerCase())
    }
  }
  str = str.replace(new RegExp(before, ''), after)
  return str;
}

myReplace("A quick brown fox jumped over the lazy dog", "jumped", "leaped");

```