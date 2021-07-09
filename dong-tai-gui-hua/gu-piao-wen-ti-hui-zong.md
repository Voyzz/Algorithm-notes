# 股票问题汇总

## 思路

```javascript
dp[i][k][1] 的含义就是：今天是第i天，我现在手上持有着股票，至今最多进行 k 次交易。
dp[i][k][0] 的含义就是：今天是第i天，我现在手上没有着股票，至今最多进行 k 次交易。

状态转移方程:
dp[i][k][0] = max(dp[i-1][k][0], dp[i-1][k][1] + prices[i])
              max(   选择 rest  ,           选择 sell      )
解释：今天我没有持有股票，有两种可能：
要么是我昨天就没有持有，然后今天选择 rest，所以我今天还是没有持有；
要么是我昨天持有股票，但是今天我 sell 了，所以我今天没有持有股票了。


dp[i][k][1] = max(dp[i-1][k][1], dp[i-1][k-1][0] - prices[i])
              max(   选择 rest  ,           选择 buy         )
解释：今天我持有着股票，有两种可能：
要么我昨天就持有着股票，然后今天选择 rest，所以我今天还持有着股票；
要么我昨天本没有持有，但今天我选择 buy，所以今天我就持有股票了。

for 0 <= i < n: 
    for 1 <= k <= K: 
        for s in {0, 1}: 
            dp[i][k][s] = max(buy, sell, rest)

base case：
dp[-1][k][0] = dp[i][0][0] = 0 
dp[-1][k][1] = dp[i][0][1] = -infinity 

核心代码：
for (let i = 1; i < n; i++){
    //卖出时利润：求最大值（上次交易卖出时利润，本次交易卖出时利润）
    profit_out = Math.max(profit_out, profit_in + prices[i]);
    //买入时利润：求最大值（上次买入时利润，本次买入时利润）
    profit_in = Math.max(profit_in,  - prices[i]);
}
```

### 一次交易

[买卖股票的最佳时机 I](https://leetcode-cn.com/problems/best-time-to-buy-and-sell-stock/submissions/)

```javascript
// k=1
function maxProfit(prices: number[]): number {
    const days:number = prices.length;

    let dp_i_1:number = -prices[0],
        dp_i_0:number = 0;

    for(let i:number=1;i<days;i++){
        dp_i_0 = Math.max(dp_i_0,dp_i_1+prices[i]);
        dp_i_1 = Math.max(dp_i_1,-prices[i])
    }

    return dp_i_0
};
```

### 交易次数无限

[买卖股票的最佳时机 II](https://leetcode-cn.com/problems/best-time-to-buy-and-sell-stock-ii/)

```javascript
// k=Inf
1. 只要股票价格上涨，上涨的部分就是我的利润，可以理解为上涨期间第一天买入，然后一直持有到上涨最后一天即下跌前一天再卖出
2. 只要股票价格下跌，那我肯定在下跌前一天卖了，而且下跌期间永远不会买入
var maxProfit = function(prices) {
  let profit = 0;
  for (let i = 0; i < prices.length - 1; i++) {
    if (prices[i + 1] > prices[i]) profit += prices[i + 1] - prices[i];
  }
  return profit;
};
```

### 两次交易

[买卖股票的最佳时机 III](https://leetcode-cn.com/problems/best-time-to-buy-and-sell-stock-iii/)

```javascript
// max_k=2
var maxProfit = function(prices) {
    //第一次 买入， 卖出的利润
    let profit_1_in = -prices[0], profit_1_out = 0;
    //继第一次之后，第二次买入卖出的利润
    let profit_2_in = -prices[0], profit_2_out = 0;
    let n = prices.length;
    for (let i = 1; i < n; i++){
        profit_2_out = Math.max(profit_2_out, profit_2_in + prices[i]);
        //第二次买入后的利润， 第一次卖出的利润 - prices[i]
        profit_2_in = Math.max(profit_2_in, profit_1_out - prices[i]);
        profit_1_out = Math.max(profit_1_out, profit_1_in + prices[i]);
        //第一次买入后，利润为 -prices[i]
        profit_1_in = Math.max(profit_1_in, -prices[i]);
    }
    return profit_2_out;
};
```

### k次交易

[买卖股票的最佳时机 IV](https://leetcode-cn.com/problems/best-time-to-buy-and-sell-stock-iv/)

```javascript
var maxProfit = function(k, prices) {
    let n = prices.length;
    if (k > n / 2) {
        k = Math.floor(n/2);  //这样也可以，但其实增加了时间复杂度和内存消耗
        // return maxProfit_k_infinity(prices); //也可以
    }
    let profit = new Array(k);
    //初始化买入卖出时的利润
    for (let j = 0; j <= k; j++){
        profit[j] = {
            profit_in: -prices[0],
            profit_out: 0
        };
    }
    for (let i = 0; i < n; i++){
        for (let j = 1; j <= k; j++){
            profit[j] = {
                profit_out: Math.max(profit[j].profit_out, profit[j].profit_in + prices[i]), 
                profit_in: Math.max(profit[j].profit_in, profit[j-1].profit_out - prices[i])
            }
        }
    }
    return profit[k].profit_out;
};
```

### 含冻结期

[含冷冻期](https://leetcode-cn.com/problems/best-time-to-buy-and-sell-stock-with-cooldown/)

```javascript
var maxProfit = function(prices) {
    let n = prices.length;
    let profit_in = 0 - prices[0];
    let profit_out = 0;
    //冻结时的利润
    let profit_freeze = 0;
    for (let i = 1; i < n; i++){
        let temp = profit_out;
        profit_out = Math.max(profit_out, profit_in + prices[i]);
        //买入时的利润= 上次冻结时的利润 - 当天价格
        profit_in = Math.max(profit_in, profit_freeze - prices[i]);
        //冻结时的利润 = 上次卖出时的利润
        profit_freeze = temp;
    }
    return profit_out;
};
```

### 含手续费

```javascript
var maxProfit = function(prices, fee) {
    //初始利润
    var profit_in = 0 - prices[0];
    var profit_out = 0;
    for (let i = 1; i < prices.length; i++){
        ////卖出： 当前买入状态时的利润 + 卖出的股票 - 手续费
        profit_out = Math.max(profit_out ,profit_in + prices[i] - fee); 
        //买入： 当前卖出时的利润 - 买进的股票
        profit_in = Math.max(profit_in ,profit_out - prices[i]);     
    }
    return profit_out;
};
```

