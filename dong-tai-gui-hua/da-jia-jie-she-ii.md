# 打家劫舍 II

## [LeetCode 213. 打家劫舍 II](https://leetcode-cn.com/problems/house-robber-ii/)

### 题目

```javascript
你是一个专业的小偷，计划偷窃沿街的房屋，每间房内都藏有一定的现金。这个地方所有的房屋都 围成一圈 ，这意味着第一个房屋和最后一个房屋是紧挨着的。同时，相邻的房屋装有相互连通的防盗系统，如果两间相邻的房屋在同一晚上被小偷闯入，系统会自动报警 。

给定一个代表每个房屋存放金额的非负整数数组，计算你 在不触动警报装置的情况下 ，今晚能够偷窃到的最高金额。



示例 1：

输入：nums = [2,3,2]
输出：3
解释：你不能先偷窃 1 号房屋（金额 = 2），然后偷窃 3 号房屋（金额 = 2）, 因为他们是相邻的。
示例 2：

输入：nums = [1,2,3,1]
输出：4
解释：你可以先偷窃 1 号房屋（金额 = 1），然后偷窃 3 号房屋（金额 = 3）。
     偷窃到的最高金额 = 1 + 3 = 4 。
示例 3：

输入：nums = [0]
输出：0
```

### 题解

#### DP

```javascript
/**
 * @param {number[]} nums
 * @return {number}
 */
var rob = function(nums) {
    if(nums.length<2) return nums[0]
    return Math.max(rob_basic(nums.slice(1)),rob_basic(nums.slice(0,-1)))
};

var rob_basic = function(nums) {
    // dp[i]=max(dp[i-2]+nums[i],dp[i-1])
    // dp[0]=nums[0],dp[1]=max(nums[1],nums[0])
    if(nums.length<3) return nums.length<2 ? nums[0] : Math.max(nums[0],nums[1])

    let len = nums.length,
        dp_i = 0,
        dp_0 = nums[0],
        dp_1 = Math.max(nums[0],nums[1]);

    for(let i=2;i<len;i++){
        dp_i = Math.max(dp_0+nums[i],dp_1);
        dp_0 = dp_1;
        dp_1 = dp_i;
    }

    return dp_i
}
```

