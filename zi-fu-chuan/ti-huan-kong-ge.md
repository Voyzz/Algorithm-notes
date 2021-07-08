# 替换空格

## 剑指 Offer 05. 替换空格

### 题目

```javascript
请实现一个函数，把字符串 s 中的每个空格替换成"%20"。



示例 1：

输入：s = "We are happy."
输出："We%20are%20happy."


限制：

0 <= s 的长度 <= 10000
```

### 解答

#### 字符串拼接

```javascript
/**
 * @param {string} s
 * @return {string}
 */
var replaceSpace = function(s) {
    let res = '';

    for (const val of s){
        if(val === " "){
            res += '%20';
        }else{
            res += val
        }
    }

    return res

};
```

#### 正则

```javascript
/**
 * @param {string} s
 * @return {string}
 */
var replaceSpace = function(s) {
    return s.replace(/\s/g,"%20")
};
```

