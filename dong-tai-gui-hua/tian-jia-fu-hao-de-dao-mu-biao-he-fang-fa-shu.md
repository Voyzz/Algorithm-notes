# 添加符号得到目标和方法数

## LeetCode 494. 目标和

### 题目

[链接](https://leetcode-cn.com/problems/target-sum/)

```text
给定一个非负整数数组，a1, a2, ..., an, 和一个目标数，S。现在你有两个符号 + 和 -。对于数组中的任意一个整数，你都可以从 + 或 -中选择一个符号添加在前面。

返回可以使最终数组和为目标数 S 的所有添加符号的方法数。

示例：

输入：nums: [1, 1, 1, 1, 1], S: 3
输出：5
解释：

-1+1+1+1+1 = 3
+1-1+1+1+1 = 3
+1+1-1+1+1 = 3
+1+1+1-1+1 = 3
+1+1+1+1-1 = 3

一共有5种方法让最终目标和为3。
```

### 题解

#### 动态规划

```text
sum(A) - sum(B) = target
sum(A) = target + sum(B)
sum(A) + sum(A) = target + sum(B) + sum(A)
2 * sum(A) = target + sum(nums)

sum(A) = (target + sum(nums)) / 2

原问题转化成：nums 中存在几个子集 A，使得 A 中元素的和为 (target + sum(nums)) / 2

dp[nums.length][sum(A)]
```

```text
dp[i][j] = dp[i-1][j]（拿第i个） + dp[i-1][j-nums[i-1]]（不拿第i个）;
dp[0][...] = 0（没有选择）;
dp[...][0] = 1 (选择不拿);
```

```javascript
var findTargetSumWays = function(nums, S) {
    const sum = nums.reduce((a,b)=>a+b);
    if((sum+S)%2 === 1 || sum < S) return 0;

    const capacity = (S+sum)/2;
    const dp = new Array(nums.length+1).fill(JSON.stringify(new Array(capacity+1).fill(0))).map(e=>JSON.parse(e));
    for(let i=0;i<=nums.length;i++){
        dp[i][0] = 1;
    }

    for(let i=1;i<nums.length+1;i++){
        for(let j=0;j<capacity+1;j++){
            if(j >= nums[i-1]){
                dp[i][j] = dp[i-1][j-nums[i-1]] + dp[i-1][j];
            }else{
                dp[i][j] = dp[i-1][j]
            }
        }
    }

    return dp[nums.length][capacity]
};
```

**优化**

#### 回溯算法

```text
当前结点(当前和(状态),剩下的数组(选择)):
//截止条件
if(剩下的选择为空){
    if(当前和 == target) count++
}

//遍历子节点
子节点()
```

```javascript
function findTargetSumWays(nums: number[], S: number): number {
    let count = 0;

    function backtrack(route:number,list:number[]):void{
        if(list.length === 0){
            if(route === S) count++;
            return
        }

        for(let i of [1,-1]){
            const num:number = list.pop();
            backtrack(route+(i*num),list);
            list.push(num)
        }
    }

    backtrack(0,nums);
    return count;
};
```

