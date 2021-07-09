# 爬楼梯

假设你正在爬楼梯。需要 n 阶你才能到达楼顶。 每次你可以爬 1 或 2 个台阶。你有多少种不同的方法可以爬到楼顶呢

```javascript
dp[0] = 0 dp[1] = 1 dp[2] = 2
dp[n] = dp[n-1] + dp[n-2]   // 到达第n阶楼梯有从n-1阶走一步和从第n-2阶走两步两种情况

var climbStairs = function(n) {
    let dp = [];
    dp[0] = 0,dp[1] = 1,dp[2] = 2;
    for(let i = 3;i <= n;i++){
        dp[i] = dp[i-2] + dp[i-1];
    }
    return dp[n];
};
```

