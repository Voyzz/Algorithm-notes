# 剑指 Offer 50. 第一个只出现一次的字符

## 题目

```JavaScript
在字符串 s 中找出第一个只出现一次的字符。如果没有，返回一个单空格。 s 只包含小写字母。

示例:

s = "abaccdeff"
返回 "b"

s = "" 
返回 " "
 

限制：

0 <= s 的长度 <= 50000

相关标签
哈希表
```

## 题解

### 哈希表

```JavaScript
/**
 * @param {string} s
 * @return {character}
 */
var firstUniqChar = function(s) {
    const hashMap = new Map();

    for (const val of s){
        // 没出现过 或出现超过一次的为false
        hashMap.set(val,!hashMap.has(val));
    }
    for (const val of s){
        if(hashMap.get(val)) return val;
    }

    return " "
};
```
