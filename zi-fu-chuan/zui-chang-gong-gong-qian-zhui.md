# 最长公共前缀

[最长公共前缀](https://leetcode-cn.com/problems/longest-common-prefix/)

编写一个函数来查找字符串数组中的最长公共前缀。 如果不存在公共前缀，返回空字符串 ""

```javascript
var longestCommonPrefix = function(strs) {
    if(!strs.length) return '';
    strs.sort();
    let a = strs[0],b = strs[strs.length-1],res = '';
    for(let i = 0;i < a.length;i++){
        if(i < b.length && a[i] === b[i]){
            res += a[i];
        }else break;
    }
    return res;
};
```

