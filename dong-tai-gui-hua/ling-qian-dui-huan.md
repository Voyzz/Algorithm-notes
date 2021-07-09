# 零钱兑换

[零钱兑换](https://leetcode-cn.com/problems/coin-change/)

给定不同面额的硬币 coins 和一个总金额 amount。编写一个函数来计算可以凑成总金额所需的最少的硬币个数。如果没有任何一种硬币组合能组成总金额，返回 -1

```javascript
// dp[0] = 0 金额为零时不需要硬币
// dp[n] = min(dp[n],dp[n-coin1] + 1，dp[n-coin2],...)  金额为n时，硬币数等于(n-coin)+1中所需硬币最少的组合

var coinChange = function(coins, amount) {
  let dp = new Array( amount + 1 ).fill( Infinity );
  dp[0] = 0;
  
  for (let i = 1; i <= amount; i++) {
    for (let coin of coins) {
      if (i - coin >= 0) {
        dp[i] = Math.min(dp[i], dp[i - coin] + 1);
      }
    }
  }
  
  return dp[amount] === Infinity ? -1 : dp[amount];
}
```

