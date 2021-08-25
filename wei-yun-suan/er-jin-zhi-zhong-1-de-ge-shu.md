# 二进制中 1 的个数

## 剑指 Offer 15. 二进制中 1 的个数

### 题目

```text
请实现一个函数，输入一个整数（以二进制串形式），输出该数二进制表示中 1 的个数。例如，把 9 表示成二进制是 1001，有 2 位是 1。因此，如果输入 9，则该函数输出 2。



示例 1：

输入：00000000000000000000000000001011
输出：3
解释：输入的二进制串 00000000000000000000000000001011 中，共有三位为 '1'。
示例 2：

输入：00000000000000000000000010000000
输出：1
解释：输入的二进制串 00000000000000000000000010000000 中，共有一位为 '1'。
示例 3：

输入：11111111111111111111111111111101
输出：31
解释：输入的二进制串 11111111111111111111111111111101 中，共有 31 位为 '1'。


提示：

输入必须是长度为 32 的 二进制串 。


注意：本题与主站 191 题相同：https://leetcode-cn.com/problems/number-of-1-bits/

相关标签
位运算
```

### 题解

#### 正则

```javascript
/**
 * @param {number} n - a positive integer
 * @return {number}
 */
var hammingWeight = function(n) {
    const len = n.toString(2).match(/1/g,'');
    return !!len ? len.length : 0
};
```

#### 位运算

```javascript
/**
 * @param {number} n - a positive integer
 * @return {number}
 */
var hammingWeight = function(n) {
    let count = 0;

    while(n != 0){
        // 通过与 1 进行与运算，可以判断末位是不是 1
        if(n & 1) count++;
        n = n >>> 1
    }

    return count
};
```
