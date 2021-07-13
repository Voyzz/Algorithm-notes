# 不用加减乘除做加法

## 剑指 Offer 65. 不用加减乘除做加法

### 题目

```text
写一个函数，求两个整数之和，要求在函数体内不得使用 “+”、“-”、“*”、“/” 四则运算符号。



示例:

输入: a = 1, b = 1
输出: 2


提示：

a, b 均可能是负数或 0
结果不会溢出 32 位整数
```

### 题解

#### 位运算

```javascript
/**
 * @param {number} a
 * @param {number} b
 * @return {number}
 */
var add = function(a, b) {
    // sum = a + b
    //     = n + c
    // n为无进位和： a ^ b
    // c为进位和：   (a & b)<<1
    // 直至c为0时 sum = n   
    let n = a^b,
        c = (a&b)<<1;
    while(c){
        const _n = n,_c = c;
        n ^= c;
        c = (_n & _c)<<1;
    }
    return n
};
```

```text
1. ^ 不进位的加法
2. & 判断进位点
3. << 1 进位
function Add(num1, num2)
{
    return num2 ? Add(num1 ^ num2,(num1 & num2) << 1) : num1;
}
```

