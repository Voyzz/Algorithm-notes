# 丑数

## 剑指 Offer 49. 丑数

### 题目

```text
我们把只包含质因子 2、3 和 5 的数称作丑数（Ugly Number）。求按从小到大的顺序的第 n 个丑数。



示例:

输入: n = 10
输出: 12
解释: 1, 2, 3, 4, 5, 6, 8, 9, 10, 12 是前 10 个丑数。
说明:  

1 是丑数。
n 不超过1690。
注意：本题与主站 264 题相同：https://leetcode-cn.com/problems/ugly-number-ii/

相关标签
数学
```

### 题解

#### DP

```javascript
// dp[i] = Min(2*dp[p2],3*dp[p3],5*dp[p5])
function nthUglyNumber(n: number): number {
    const dp:number[] = [];
    let p2 = 0,
        p3 = 0,
        p5 = 0;
    dp[0] = 1;

    for(let i:number = 1;i<n;i++){
        const _min:number = Math.min(2*dp[p2],Math.min(3*dp[p3],5*dp[p5]));
        dp[i] = _min;
        if(_min == 2*dp[p2]) p2++;
        if(_min == 3*dp[p3]) p3++;
        if(_min == 5*dp[p5]) p5++;
    }

    return dp[n-1]
};
```

