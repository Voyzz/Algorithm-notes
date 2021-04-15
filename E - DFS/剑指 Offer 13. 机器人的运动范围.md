# 剑指 Offer 13. 机器人的运动范围
## 题目
```
地上有一个m行n列的方格，从坐标 [0,0] 到坐标 [m-1,n-1] 。一个机器人从坐标 [0, 0] 的格子开始移动，它每次可以向左、右、上、下移动一格（不能移动到方格外），也不能进入行坐标和列坐标的数位之和大于k的格子。例如，当k为18时，机器人能够进入方格 [35, 37] ，因为3+5+3+7=18。但它不能进入方格 [35, 38]，因为3+5+3+8=19。请问该机器人能够到达多少个格子？

 

示例 1：

输入：m = 2, n = 3, k = 1
输出：3
示例 2：

输入：m = 3, n = 1, k = 0
输出：1
提示：

1 <= n,m <= 100
0 <= k <= 20
```

## 题解
### DFS 递归
```
/**
 * @param {number} m
 * @param {number} n
 * @param {number} k
 * @return {number}
 */
var movingCount = function(m, n, k) {
    // 辅助矩阵记录已标记点
    const visted = new Array(m).fill(JSON.stringify(new Array(n))).map(res => {return JSON.parse(res)})

    
    const dfs = function(row,column){
        // 截止条件: 越界或已标记过 返回0
        if(row<0 || row>=m || column<0 || column>=n || getSum(row)+getSum(column) > k || visted[row][column]) return 0;
        // 标记
        visted[row][column] = true;

        // 递归
        return dfs(row+1,column)+dfs(row,column+1)+1
    }

    const getSum = function(val){
        return Math.floor(val/10) + val%10;
    }
    return dfs(0,0);
};
```