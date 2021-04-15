# 剑指 Offer 10 - II. 青蛙跳台阶问题
## 题目
```
一只青蛙一次可以跳上1级台阶，也可以跳上2级台阶。求该青蛙跳上一个 n 级的台阶总共有多少种跳法。

答案需要取模 1e9+7（1000000007），如计算初始结果为：1000000008，请返回 1。

示例 1：

输入：n = 2
输出：2
示例 2：

输入：n = 7
输出：21
示例 3：

输入：n = 0
输出：1
提示：

0 <= n <= 100
注意：本题与主站 70 题相同：https://leetcode-cn.com/problems/climbing-stairs/

 

相关标签
递归
```

## 题解
### 动态规划
```
/**
 * @param {number} n
 * @return {number}
 */
var numWays = function(n) {
    const dp = [];
    dp[0] = 1;
    dp[1] = 1;
    
    for(let i=2;i<n+1;i++){
        dp[i] = (dp[i-1] + dp[i-2])%1000000007
    }

    return dp[n]
};
```

### 动态规划（空间优化）
```
function numWays(n: number): number {
    if(n < 2) return 1;
    let p1:number = 1,
        p2:number = 1,
        res:number;
    
    for(let i=1;i<n;i++){
        res = (p1+p2)%1000000007;
        p1 = p2;
        p2 = res;
    }

    return res;
};
```