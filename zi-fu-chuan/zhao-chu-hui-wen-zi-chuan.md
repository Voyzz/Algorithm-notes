# 找出回文子串

[回文子串](https://leetcode-cn.com/problems/palindromic-substrings/)

给定一个字符串，你的任务是计算这个字符串中有多少个回文子串。 具有不同开始位置或结束位置的子串，即使是由相同的字符组成，也会被计为是不同的子串。

```javascript
var countSubstrings = function(s) {
    let s2 = s.split('').reverse().join('');
    let sum = 0;
    const len = s.length;
    for (let i = 0; i < len; i++) {
        for (let j = i + 1; j <= len; j++) {
            if (s.substr(i, j - i) === s2.substr(len - j, j - i)) {
                sum += 1
            }
        }
    }
    return sum;
};
```

