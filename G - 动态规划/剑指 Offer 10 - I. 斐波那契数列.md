# 剑指 Offer 10 - I. 斐波那契数列
## 题目
```
写一个函数，输入 n ，求斐波那契（Fibonacci）数列的第 n 项（即 F(N)）。斐波那契数列的定义如下：

F(0) = 0,   F(1) = 1
F(N) = F(N - 1) + F(N - 2), 其中 N > 1.
斐波那契数列由 0 和 1 开始，之后的斐波那契数就是由之前的两数相加而得出。

答案需要取模 1e9+7（1000000007），如计算初始结果为：1000000008，请返回 1。

 

示例 1：

输入：n = 2
输出：1
示例 2：

输入：n = 5
输出：5
 

提示：

0 <= n <= 100
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
var fib = function(n) {
    let dp = []
    dp[0] = 0;
    dp[1] = 1;
    for(let i=2;i<n+1;i++){
        dp[i] = (dp[i-1]+dp[i-2])% 1000000007
    }
    return dp[n]
};
```

### 动态规划（空间优化）
```
function fib(n: number): number {
    if(!n) return 0;
    let p1:number = 0,
        p2:number = 1,
        res:number = 1;
    
    for(let i=0;i<n-1;i++){
        res = (p1+p2)%1000000007;
        p1 = p2;
        p2 = res;
    }

    return res;
};
```