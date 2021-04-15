# LeetCode 322. 零钱兑换
## 题目
```
给定不同面额的硬币 coins 和一个总金额 amount。编写一个函数来计算可以凑成总金额所需的最少的硬币个数。如果没有任何一种硬币组合能组成总金额，返回 -1。

你可以认为每种硬币的数量是无限的。

 

示例 1：

输入：coins = [1, 2, 5], amount = 11
输出：3 
解释：11 = 5 + 5 + 1
示例 2：

输入：coins = [2], amount = 3
输出：-1
示例 3：

输入：coins = [1], amount = 0
输出：0
示例 4：

输入：coins = [1], amount = 1
输出：1
示例 5：

输入：coins = [1], amount = 2
输出：2
```

## 题解
### 动态规划
![cea394cc79d01b81d7615da4de3f24e4.png](evernotecid://849303AB-DE4A-407B-BB36-67ADB0B253A4/appyinxiangcom/24827522/ENResource/p448)

```
var coinChange = function(coins, amount) {
    const dp = new Array(amount+1).fill(amount+1);
    dp[0] = 0;

    for(let n=0;n<=amount;n++){
        for(let i=0;i<coins.length;i++){
            if(n-coins[i] < 0) continue;
            dp[n] = Math.min(dp[n],dp[n-coins[i]]+1);
        }
    }

    return dp[amount] == amount+1 ? -1 : dp[amount]
};
```