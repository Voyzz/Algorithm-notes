# 剑指 Offer 46. 把数字翻译成字符串
## 题目
```
给定一个数字，我们按照如下规则把它翻译为字符串：0 翻译成 “a” ，1 翻译成 “b”，……，11 翻译成 “l”，……，25 翻译成 “z”。一个数字可能有多个翻译。请编程实现一个函数，用来计算一个数字有多少种不同的翻译方法。

 

示例 1:

输入: 12258
输出: 5
解释: 12258有5种不同的翻译，分别是"bccfi", "bwfi", "bczi", "mcfi"和"mzi"
 

提示：

0 <= num < 231
```

## 题解
### DP
```
// dp[i]: 至数字第i位共有多少种组合
// 如果num第(i-2)位到第i位 是在10~25区间: dp[i] = dp[i-1]+dp[i-2]
// 否则: dp[i] = dp[i-1]

function translateNum(num: number): number {
    const dp:number[] = [],numStr:string = num.toString();
    dp[0] = 1;
    dp[1] = 1;

    for(let i=2;i<=numStr.length;i++){
        const subNum:number = parseInt(numStr.substr(i-2,2));
        if(9<subNum && subNum<26) dp[i] = dp[i-1]+dp[i-2];
        else dp[i] = dp[i-1];
    }

    return dp[numStr.length]
};
```