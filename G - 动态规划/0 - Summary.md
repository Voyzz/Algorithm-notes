```
* 【状态】和【选择】
* ✨ 动态规划其实是相对于递归的穷举做了优化，将前面的值缓存下来，后面再使用时不需要再从底层重复算一遍。
* ✨ 能用动态规划解决的问题
    * 问题的答案依赖于问题的规模，也就是问题的所有答案构成了一个数列。
    * 大规模问题的答案可以由小规模问题的答案递推得到，也就是的值可以由中的个别求得。
* ✨ 应用动态规划——将动态规划拆分成三个子目标
    * 建立状态转移方程
        * 注意dp[i]是最大的值
    * 缓存并复用以往结果
        * 要定义初始状态
    * 按顺序从小往大算
* 当只需获取dp的最后一个值时可改写
var lastRemaining = function(n, m) {
    const dp = [];
    dp[1] = 0;


    for(let i=2;i<=n;i++){
        dp[i] = (dp[i-1]+m)%i;
    }


    return dp[n]
};


var lastRemaining = function(n, m) {
    let res = 0;


    for(let i=2;i<=n;i++){
        res = (res+m)%i;
    }


    return res
};


```