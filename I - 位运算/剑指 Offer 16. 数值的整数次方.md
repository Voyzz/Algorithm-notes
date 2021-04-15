# 剑指 Offer 16. 数值的整数次方
## 题目
```
实现函数double Power(double base, int exponent)，求base的exponent次方。不得使用库函数，同时不需要考虑大数问题。

 

示例 1:

输入: 2.00000, 10
输出: 1024.00000
示例 2:

输入: 2.10000, 3
输出: 9.26100
示例 3:

输入: 2.00000, -2
输出: 0.25000
解释: 2-2 = 1/22 = 1/4 = 0.25
 

说明:

-100.0 < x < 100.0
n 是 32 位有符号整数，其数值范围是 [−231, 231 − 1] 。
注意：本题与主站 50 题相同：https://leetcode-cn.com/problems/powx-n/

相关标签
递归
```

## 题解
### 快速幂 递归

```
/**
 * @param {number} x
 * @param {number} n
 * @return {number}
 */
var myPow = function(x, n) {
    // x^n = x^n * res 
    // x^n = (x^2)^(n除2) * (奇x偶1)
    // ...
    // x^n = (x^...)^0 * res;
    if(n == 0) return 1;
    if(n < 0) return 1/myPow(x,-n);
    
    if(n % 2 == 0){
        return myPow(x*x,n/2);
    }else{
        return x*myPow(x,n-1);
    }
};
```